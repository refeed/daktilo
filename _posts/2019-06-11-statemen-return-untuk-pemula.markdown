---
layout: post
title:  "Apa Itu Statement `return`, Fungsinya?"
subtitle: "Fungsi statemen return pada sebuah fungsi"
date:   2019-06-11 00:00:00+7
categories: [indonesian, programming]
---

"*Statemen return* apa fungsinya?" Banyak pemula yang di saat memulai jalannya
di programming kebingungan saat memahami apa itu *statemen `return`* dan
fungsinya. Sejujurnya saya juga memerlukan waktu beberapa saat untuk mengerti
tentang fungsi dari *statement* `return` ini. Mungkin banyak orang Indonesia
yang memahami *statemen `return`* dengan cara menerjemahkannya ke bahasa
Indonesia, menjadi "kembali", "mengembalikan", dan lain-lain. Yup, itu bisa
saja benar, tetapi kita perlu lihat seperti apa "mengembalikan" yang dimaksud
di sini.

Pertama-tama yang harus seseorang tahu untuk mengerti fungsi dari `return`
adalah statemen ini banyak kaitannya dengan fungsi (`function`) di dalam
pemrograman. Tidak ada statement `return` yang muncul di luar fungsi, hal ini
menunjukan bahwa `return` adalah sebuah bagian daripada sebuah fungsi.

Sekarang kita lihat lagi apa itu fungsi (`function`). Fungsi biasa digunakan
agar sebuah bagian daripada sebuah program bisa digunakan berulang kali. Fungsi
yang tidak menghasilkan nilai apapun bisa disebut dengan `method` (metode).

Misal kita ingin menghitung luas lingkaran-lingkaran, kita diberikan jari-jari
dari lingkaran-lingkaran tersebut.

```py
# Kita bisa menuliskan
jari1 = 7
luas1 = 3.14 * (jari1**2)

jari2 = 8
luas2 = 3.14 * (jari2**2)

jari3 = 9
luas3 = 3.14 * (jari3**2)

print("luas1 = %d, luas2 = %d, luas3 = %d" % (luas1, luas2, luas3))
```

Bisa melihat dimana perulangannya? Ya, perulangannya ada pada pernyataan dalam
menghitung luas jari-jarinya (`luas1`, `luas2`, `luas3`). Mereka semua sama,
sehingga langkah tersebut bisa kita jadikan sebuah fungsi. Cek kode di bawah.

```py
def hitung_luas_lingkaran(jari_jari):
    return 3.14 * (jari_jari**2)  # pi * jari-jari^2

jari1 = 7
luas1 = hitung_luas_lingkaran(jari1)

jari2 = 8
luas2 = hitung_luas_lingkaran(jari2)

jari3 = 9
luas3 = hitung_luas_lingkaran(jari3)

print("luas1 = %d, luas2 = %d, luas3 = %d" % (luas1, luas2, luas3))

```

Jika Anda menjalankan kedua program tersebut, mereka akan menghasilkan hasil
yang sama (nilai variabel-variabel dan string yang diprint ke console).

```console
luas1 = 153, luas2 = 200, luas3 = 254
```

Sudah mendapat gambaran tentang *statement* `return` ini? Pada dasarnya
statemen ini mengembalikan (meng-`output`) sebuah nilai, sehingga nilai
tersebut nantinya bisa digunakan oleh bagian lain dari sebuah program. Perlu
diketahui juga, fungsi hanya bisa mengeluarkan sebuah nilai[1], yang artinya
hanya akan ada satu *statement* `return` yang dijalankan meskipun ada banyak
statement return pada sebuah fungsi.

Lihat kode di bawah.

```py
def hitung_luas_lingkaran(jari_jari):
    return 3.14 * (jari_jari**2)  # pi * jari-jari^2
    return 'refeeeeeeeeeeeeeeeeed'

jari1 = 7
luas1 = hitung_luas_lingkaran(jari1)

jari2 = 8
luas2 = hitung_luas_lingkaran(jari2)

jari3 = 9
luas3 = hitung_luas_lingkaran(jari3)

print("luas1 = %d, luas2 = %d, luas3 = %d" % (luas1, luas2, luas3))
```

Pada fungsi `hitung_luas_lingkaran` yang sudah dimodifikasi di atas, kita
memiliki dua *statement* `return`, lalu mana *statement* `return` yang akan
dijalankan? Seperti yang dikatakan sebelumnya, hanya akan ada satu `return`
yang akan dijalankan, yang artinya setelah sebuah statement `return` dijalankan
di sebuah fungsi maka fungsi tersebut sudah selesai dijalankan. Umumnya program
mengeksekusi kode dari atas ke bawah secara berurutan, jadi hanya statement
`return` yang atas saja yang dijalankan, setelah itu fungsi sudah selesai
dijalankan.

Anda bisa menjalankan kode di atas dan masih mendapatkan hasil yang sama dengan
sebelumnya.

## Fungsi yang tidak memiliki `return`

Ada juga fungsi yang tidak memiliki *statement* `return`, fungsi ini umumnya
disebut `method` karena hanya menjalankan langkah-langkah yang ada di dalam
fungsinya dan tidak menghasilkan nilai apapun.

Lihat kode di bawah

```py
buah = ['jeruk', 'mangga', 'lemon']
buah.append('naga')

hewan = ['kucing', 'jerapah']
hewan.append('naga')

print('buah = ', buah)
print('hewan = ', hewan)
```

Kita bisa mengubah program tersebut menjadi seperti kode di bawah.

```py
def tambah_naga(array):
    array.append('naga')

buah = ['jeruk', 'mangga', 'lemon']
tambah_naga(buah)

hewan = ['kucing', 'jerapah']
tambah_naga(hewan)

print('buah = ', buah)
print('hewan = ', hewan)
```

Kedua program di atas akan mencetak string yang sama ke console yaitu:
```console
buah =  ['jeruk', 'mangga', 'lemon', 'naga']
hewan =  ['kucing', 'jerapah', 'naga']
```

Jika kita lihat ke fungsi `tambah_naga` di atas, tidak ada *statement* `return`
yang tertulis sehingga fungsi ini tidak akan menghasilkan sebuah nilai apabila
kita masukkan nilai tersebut ke variabel, contoh:

```py
def tambah_naga(array):
    array.append('naga')

buah = ['jeruk', 'mangga', 'lemon']
nilai_tambah_naga = tambah_naga(buah)

print('buah = ', buah)
print('nilai_tambah_naga = ', nilai_tambah_naga)
```

Akan mencetak string berikut ke console:
```console
buah =  ['jeruk', 'mangga', 'lemon', 'naga']
nilai_tambah_naga =  None
```

Dimana bisa kita lihat bahwa nilai variable `nilai_tambah_naga` adalah `None`
(`None` adalah sebuah objek dalam `Python` yang biasa digunakan untuk
merepresentasikan ketidakadaan).

Hanya *sidenote*, sebenarnya Python menambahkan `return None` pada akhir sebuah
fungsi yang tidak memiliki sebuah `return`. Anda juga bisa mengekspresikan
statement tersebut secara eksplisit dengan mengubah fungsi `tambah_naga`
menjadi:

```py
def tambah_naga(array):
    array.append('naga')
    return None
```

atau

```py
def tambah_naga(array):
    array.append('naga')
    return
```

Mereka akan menjalankan langkah yang sama dan output dari program sebelumnya
tidak berubah.

Fungsi dari method `tambah_naga` adalah menambahkan string `'naga'` ke dalam
sebuah array dan tidak mengoutput nilai apapun.

## Memanfaatkan return untuk menjaga kode agar tetap simpel

Kita bisa memanfaatkan tingkah laku *statement* `return` untuk menjaga kode
kita agar tetap simpel, seperti yang kita ketahui bahwa jika sebuah *statement*
`return` sudah dijalankan di sebuah fungsi, maka fungsi tersebut sudah selesai
dijalankan.

Misalnya kita memiliki sebuah fungsi untuk menunjukan apakah sebuah angka itu
genap atau ganjil.

```py
def apakah_genap(angka):
    if angka % 2 == 0:
        return True
    else
        return False
```

Kita juga bisa menuliskan fungsi di atas seperti di bawah ini:

```py
def apakah_genap(angka):
    if angka % 2 == 0:
        return True
    return False
```

Kedua fungsi tersebut akan menghasilkan hasil yang sama. Lebih simpel bukan?

## Apa bedanya dengan `print()` ?

Banyak pemula yang salah mengerti bahwa `print()` juga menghasilkan nilai atau
berperan layaknya `return` karena fungsi ini mencetak sebuah string ke console
mereka. Sebenarnya bukan begitu, `print()` merupakan sebuah `method`, yang
berarti fungsi ini hanya menjalankan langkah-langkah yang berkaitan dengan
mencetak sebuah string ke console, dan tidak menghasilkan nilai apa-apa
(`None`).

Lihat contoh di bawah

```py
a = print('refeed')
print(a)
```

Program tersebut akan mencetak string berikut ke console:

```console
refeed
None
```

Pada program di atas kita melihat bahwa variabel `a` akan dimasuki oleh hasil
dari *statement* `print('refeed')` dan pada baris ke-2 kita mencetak nilai dari
variabel `a`. Pada console ditampilkan `refeed` dan `None`. String `refeed`
pada console dicetak oleh *statement* `print('refeed')` dan string `None` pada
console dicetak oleh `print(a)`, yang artinya `a` bernilai `None` dan
`print('refeed')` tidak menghasilkan nilai apa-apa.

Demikian *post* kali ini, jadi intinya `return` adalah statemen yang berfungsi
untuk mengeluarkan (mengembalikan, mengoutputkan) nilai dari sebuah fungsi yang
dimana nilai yang sudah dihasilkan tadi akan diproses oleh bagian lain daripada
program.

Jika ada saran ataupun komentar, silakan tulis pada kolom komentar yang ada di
bawah artikel ini, terimakasih. Tujuan dari artikel ini adalah untuk
menjelaskan semudah-mudahnya kepada seorang pemrogram pemula yang baru
belajar pemrograman khususnya tentang statement `return`.

[1] Sebuah nilai yang dimaksud disini adalah sebuah objek, dengan kata lain
fungsi bisa saja me-`return` sebuah `list` yang berisi banyak nilai, tetapi
tetap saja `list` itu adalah sebuah objek.
