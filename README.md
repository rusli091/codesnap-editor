[![Intro](https://github.com/bokub/nopaste/raw/images/intro.png)][intro-img]

# Apa itu NoPaste?

[NoPaste](https://nopaste.boris.sh/) adalah situs web open-source mirip dengan Pastebin di mana Anda dapat menyimpan berbagai kode program dan menghasilkan tautan untuk berbagi dengan mudah.

Namun, yang membuat NoPaste istimewa adalah bahwa ia bekerja tanpa **database** dan tanpa **kode back-end**. Sebaliknya, data dikompres dan **disimpan sepenuhnya dalam tautan** yang Anda bagikan, tidak di tempat lain!

> [!CATATAN]  
> Karena semua domain `.ml` telah dihapus pada 17 Juli 2023, NoPaste telah pindah dari [nopaste.ml](https://nopaste.ml/) ke [nopaste.boris.sh](https://nopaste.boris.sh/)
>
> Anda mungkin masih bisa mengunjungi [nopaste.ml](https://nopaste.ml/) jika Anda mengunjunginya **sebelumnya** dengan **browser yang sama** (berkat fitur penggunaan offline), tetapi tidak akan berfungsi untuk pengunjung baru.
>
> Tentu saja, semua tautan lama Anda akan terus berfungsi jika Anda hanya mengganti `nopaste.ml` dengan `nopaste.boris.sh`!
>
> Maaf atas gangguan, dan terima kasih atas pengertian Anda!

### Karena desain ini:

- 🗑️ Data Anda **tidak dapat dihapus** dari NoPaste
- 🔞 Data Anda **tidak dapat disensor**
- 👁️ Server yang menghosting NoPaste (atau kloning darinya) **tidak dapat membaca atau mengakses** data Anda
- ⏳ Data Anda akan dapat diakses **selamanya** (selama Anda memiliki tautannya)
- 🔀 Anda dapat mengakses data Anda di **setiap klon NoPaste**, termasuk [milik Anda sendiri](https://github.com/bokub/nopaste/wiki/Deploy-your-own-version-of-NoPaste)
- 🔍 Google **tidak akan mengindeks** data Anda, bahkan jika tautan Anda bersifat publik

> **Catatan:** Proyek ini adalah salinan dari [layanan paste Topaz][topaz-example], dengan desain yang dimodifikasi dan beberapa fitur tambahan (penyorotan sintaks, nomor baris, penggunaan offline, penyematan...)

## Cara kerjanya

Ketika Anda mengklik "Generate Link", NoPaste mengompres seluruh teks menggunakan [algoritma LZMA](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Markov_chain_algorithm), mengenkodenya dalam [Base64](https://en.wikipedia.org/wiki/Base64), dan menempatkannya di fragmen URL opsional, setelah simbol `#` pertama: `nopaste.boris.sh/#<data Anda di sini>`

Ketika Anda membuka tautan, NoPaste membaca, mendekode, dan mendekompresi apa pun yang ada setelah `#`, dan menampilkan hasilnya di editor.

Proses ini dilakukan sepenuhnya **di browser Anda**, dan server web yang menghosting NoPaste [tidak pernah memiliki akses ke fragmen](https://en.wikipedia.org/wiki/Fragment_identifier)

Misalnya, [ini adalah kode CSS yang digunakan oleh NoPaste][example]

## Fitur lainnya

### Cuplikan NoPaste yang Disematkan

Anda dapat menyertakan cuplikan kode NoPaste ke dalam situs web Anda sendiri dengan mengklik tombol _Embed_ dan menggunakan kode HTML yang dihasilkan.

Berikut adalah contoh kode yang dihasilkan dan tampilannya (klik pada tangkapan layar untuk melihat versi interaktif)

```html
<iframe
    width="100%"
    height="243"
    frameborder="0"
    src="https://nopaste.boris.sh/?l=py#XQAAAQAbAQAAAAAAAAA0m0pnuFI8c+qagMoNTEcTIfyUWbZjtjmBYcmJSzoNwS5iVMWHzvowv3IPM0vOG5cjrtDRTSVP/0biTIrrahfmbkuMQBBeSiSGpaJOqYJiKmUDYn2Gp1RtWE6gm8fLHMB4eyZ3+rEbUQwWyMcmWqvZ7m96RUeFyZdYbE85JGvhghqF8cyPB0ZjV0OQWsDxn5O5ysMrIcL+pKPk89EtLjAHhA1LZL9F3hzAtTx7I+GlyrxhhXGxAN//CvtaAA=="
></iframe>
```

[![iframe](https://raw.githubusercontent.com/bokub/nopaste/images/pagerank.png)](https://jsfiddle.net/cqr2kxf5/)

Jangan ragu untuk mengedit atribut `height` dan `width` agar sesuai dengan kebutuhan Anda

### Penggunaan Offline

Ketika Anda mengunjungi NoPaste untuk pertama kali, kodenya disimpan dalam cache browser Anda. Setelah itu, setiap tautan NoPaste yang Anda buka akan dimuat dengan sangat cepat, bahkan jika koneksi internet Anda lambat.

Bagaimana jika Anda sama sekali tidak memiliki koneksi internet? Tidak masalah, NoPaste akan tetap berfungsi dengan sempurna!

### Fitur Editor

- Penyorotan sintaks (gunakan pemilih bahasa)
- Aktifkan/nonaktifkan pembungkusan baris (gunakan tombol di sebelah pemilih bahasa)
- Hapus baris (`Ctrl+D`)
- Multi kursor (`Ctrl+Click`)
- Pintasan keyboard biasa (`Ctrl+A`, `Ctrl+Z`, `Ctrl+Y`...)

## Ukuran Maksimum untuk Tautan

NoPaste sangat bagus untuk berbagi cuplikan kode di berbagai platform.

Berikut adalah panjang tautan maksimum di beberapa aplikasi dan browser.

| Aplikasi | Panjang Maks |
| -------- | ------------ |
| Reddit   | 10.000       |
| Twitter  | 4.088        |
| Slack    | 4.000        |
| QR Code  | 2.610        |
| Bitly    | 2.048        |
| TinyURL  | 32.000       |

| Browser         | Panjang Maks                | Catatan                                    |
| --------------- | --------------------------- | ------------------------------------------ |
| Google Chrome   | (win) 32.779 (mac) 10.000  | Tidak akan ditampilkan, tapi tautan lebih panjang berfungsi |
| Firefox         | >64.000                     |                                            |
| Microsoft IE 11 | 4.043                       | Tidak akan menampilkan lebih dari 2.083    |
| Microsoft Edge  | 2.083                       | Apa pun di atas 2083 akan gagal            |
| Android         | 8.192                       |                                            |
| Safari          | Banyak                      |                                            |

## Membuat Tautan NoPaste

Tautan NoPaste dapat dibuat dengan mudah dari command line sistem Anda:

```bash
# Linux
echo -n 'Hello World' | lzma | base64 -w0 | xargs -0 printf "https://nopaste.boris.sh/#%s\n"

# Mac
echo -n 'Hello World' | lzma | base64 | xargs -0 printf "https://nopaste.boris.sh/#%s\n"

# Windows / WSL / Linux
echo -n 'Hello World' | xz --format=lzma | base64 -w0 | printf "https://nopaste.boris.sh/#%s\n" "$(cat -)"
```

## Menyebarkan Versi NoPaste Anda Sendiri

NoPaste hanyalah sekumpulan file statis, membuatnya sangat mudah untuk disebarkan di berbagai jenis server file.

Baca [wiki](https://github.com/bokub/nopaste/wiki/Deploy-your-own-version-of-NoPaste) untuk melihat bagaimana Anda dapat menyebarkan versi NoPaste Anda sendiri secara gratis menggunakan Github Pages.

[intro-img]: https://nopaste.boris.sh/?l=tcl#XQAAAQA6BAAAAAAAAAAFYH9MXlzSsUdj4vga48M86Ff/Bo1HzNmlXzjCWCN1Q/EliRJg00jhrYF9eDKWzDi+Su+Pv1o8yGz3V06CtGOt8u9dUN10KuOrmkUrjI/kUqitUUD34YXmq9twyrkxmOl5kaHPNqE2PWTRhnKWCEntngrOOlXC4kxxnXuGB2v4zJ75fIM0htURHr9ysHH+1nHvSRng4zpcYju3Y/RqpGTIowXGoUcIOeKKG8PpYf/9t33i
[example]: https://nopaste.boris.sh/?l=css#XQAAAQB2DQAAAAAAAAAXioAj/ZZaukKWizx++f8w08qY+xe+w0AeNB0EtEDMR1jPECOrMSz2rcy5XqUVTzusmFXo407ujwufsB1Va3cy02BV4Chx15I+SbM8Ei2WS8/MaZa0wIOjHf0s6B9Kcwi1J73qYeIcKm39PEWGnBM4Ym5aXFOF1Irrn1N95vEcl4YI+98rydudZHmsNCmt995GvCpLImwH7yj3SlMadWaQA0jHCrY1ZBvhjSJ9mAAdYjCJLduITZuXomgpqtr3sYI1WKeRGNmPSD8J8WRLtCx0BZl3yWZZrUxJbmVod8cYiPJnlO+CzQA03qA/GZnxhMYd9TPc2Xlq8UIhBX6gmvo/xhHJc/WHnuBFB32xJ37O5FZlZuXGy6wFE/lakVteoqEqgvyan4LfaiL0pMfYapWjV8YoPa/KyVGugANNjvtRw0hRr+Z1IgKoVL2a1xqvQiB65vIXkw68/ui82O1ko9HTbsLMHX/2/CgWZ8TkTEvgr0+dzVqQYIpaWpB3hDnUTHMkG2UehM5iJyJXAgODNqk8IiWCJn5k/j2FeFpchSTWdgi7AeaCowubmWnFTNgNFXLf5zzARWBUGQFT55TiC0ah4HL17jG3rY6fXvAXlm6CWc88ne7wF0opHkLnhfPslssDYo75hDmCfYwJ6asQ/YBkSuuLJjdCEXVjF7Pdw2FhsOiiB0gNXC6ehieM28M+PMGSDRqt0Q0KveMgE44YJ8zFOvpu2Gg41qDkrsYS7Xb/iMnHz66tt69I1rGzrHx88PuI2/CZx+kv+z7a+/Eiq4JC3KTDx4IbNUYptmrIOC2bxGrcjd8TBKGe+dNi8a/PEnXrUXc/OD7D680/Awo+scE8VKuRVN5R7OPg0tmKVQSQkyCf+I3//kGmREyhh6/bCv6tvbEc7hNPNE1js2svlVBF001JlLY7g1w6ls2pjxrKxuCLrkjba1n4s5WlfrbwcX18rqgbfL2tVibHggsy3Lgq4i7fXtuO3JifxfauO66YIRjEWFnACrHbZ14FbHDMylN7GMvo5TusxestU0s6+kiibWq2qZVpi7C5JVKURNQrGEabICn5nUDoOPMZSfNrdmlTOhu4qjKW09XdQPNazTMc83KjG1YOKNjRP23i1oav5muBFRGMDkSXt7wCgv5PCpLZM9w2jC5GCa5oHuH92IWJu5d80fvTRw3GxNQzfMRxgjzfH6xxrzu+EghhbzayUhb3U5aSRSxOtPTPfjT9mxgk7j3f1mRlbYheuhko4/LBIKYvfA5CnN2Yr3VyBYqoZ/ZgP871LU0ix8ZLeaecao0SDj6V35bZ6RB53mcU8BRPfcyZhj0H6BrFcrcfXKVwnNVro/cIrwnoG3GwlpCXGYJmDDeUdlbBj2HrVmvMncd3w8SzPtxw5RAWQP9YPJdE4Tc490BMX4zAkPqirRHLcxG/K5ECLtKtGsnCkg24+XwFo4XRcGfMsbkSSYD7oZ2HkD+1NXYqJKgk+7uee+yrYCZF6xbsb0ca/7r3w8nU9DueSa6XPiaCLSeJ+phw8iK1U4+FcCzqLW4LzgfcGjz64+HM+Xst0YuqzrAI2RU80H2Mr0FnC/qL+klbM+p0yNUBxBd4IQ
