LAPORAN TUGAS INDIVIDU
Manipulasi Citra Digital Menggunakan OpenCV
Mata Kuliah
Pengolahan Sinyal Digital
Disusun Oleh
Nama : Ahmad Furqon Ramadhani
NIM : 452024611066
Program Studi : Teknik Informatika
Universitas Darussalam Gontor

1. Pendahuluan
Manipulasi citra digital merupakan proses pengolahan citra menggunakan operasi matematis untuk memperoleh informasi atau meningkatkan kualitas visual citra. Pada praktikum ini digunakan library OpenCV, NumPy, dan Matplotlib untuk melakukan beberapa teknik manipulasi citra, yaitu konversi warna, resize, image blending, image negative, transformasi logaritmik, dan transformasi gamma.
Tujuan praktikum adalah memahami bagaimana perubahan nilai piksel mempengaruhi brightness, contrast, serta detail citra sehingga dapat menentukan teknik yang tepat untuk kasus tertentu.
2. Citra yang Digunakan
Eksperimen menggunakan dua buah citra digital:
•	Image 1 : pemandangan pegunungan
•	Image 2 : pemandangan kota
Kedua citra digunakan sebagai objek eksperimen pada seluruh proses manipulasi.
Library yang digunakan:
•	OpenCV
•	NumPy
•	Matplotlib

3. Membaca Citra dan Konversi Warna
Hasil
Citra berhasil dibaca menggunakan fungsi  cv.imread() dan dikonversi ke RGB menggunakan fungsi cv.cvtColor().
Output yang diperoleh:
•	Tampilan citra sebelum konversi
•	Tampilan citra setelah konversi
•	Shape citra
•	Tipe data citra
•	Nilai minimum dan maksimum piksel
Analisis
OpenCV membaca citra dalam format BGR, sedangkan Matplotlib menggunakan RGB. Jika citra langsung ditampilkan tanpa konversi maka warna akan terlihat tidak sesuai. Oleh karena itu konversi warna diperlukan sebelum visualisasi dilakukan.

4. Resize Citra
Hasil
Kedua citra diubah ukurannya menjadi 600 × 400 piksel sehingga memiliki dimensi yang sama.
Resize diperlukan agar kedua citra dapat diproses pada tahap image blending.
Analisis
Apabila ukuran citra berbeda maka operasi blending tidak dapat dilakukan karena setiap piksel harus memiliki pasangan piksel pada posisi yang sama.
Risiko resize adalah:
•	Hilangnya detail citra
•	Distorsi objek
•	Penurunan kualitas visual
5. Image Blending
Image blending dilakukan menggunakan persamaan:
Iblend = αI1 + βI2 + γ
Eksperimen dilakukan dengan tiga kombinasi bobot:
α	β
0.2	0.8
0.5	0.5
0.8	0.2
Hasil dan Analisis
α	β	Analisis
0.2	0.8	Citra kedua lebih dominan
0.5	0.5	Kedua citra seimbang
0.8	0.2	Citra pertama lebih dominan
Semakin besar nilai α maka kontribusi citra pertama semakin besar. Teknik ini banyak digunakan untuk overlay, watermark, dan efek visual.

6. Image Negative
Image negative dilakukan menggunakan persamaan:
Inegative = 255 − I
Hasil
Histogram citra menunjukkan distribusi intensitas yang terbalik dibandingkan citra asli.
Analisis
•	Area terang berubah menjadi gelap.
•	Area gelap berubah menjadi terang.
•	Distribusi histogram berpindah secara simetris.
Teknik ini berguna untuk memperjelas objek tertentu yang sulit diamati pada citra asli.

7. Transformasi Logaritmik dan Gamma
Transformasi Logaritmik
Persamaan:
s = c log(1+r)
Analisis
Transformasi logaritmik meningkatkan intensitas piksel rendah sehingga detail pada area gelap menjadi lebih terlihat.
Kelebihan:
•	Menonjolkan detail area gelap
•	Memperluas rentang intensitas rendah
Kekurangan:
•	Area terang dapat kehilangan detail jika digunakan berlebihan
Transformasi Gamma
Persamaan:
s = r^γ
Eksperimen dilakukan menggunakan:
•	γ = 0.5
•	γ = 1
•	γ = 2
•	γ = 2.5
Analisis
Gamma	Efek
0.5	Citra lebih terang
1.0	Tidak berubah
2.0	Citra lebih gelap
2.5	Citra semakin gelap
Gamma correction sangat efektif untuk menyesuaikan pencahayaan tanpa mengubah struktur utama citra.

8. Analisis HOTS, Studi Kasus, dan Kesimpulan
Perbandingan Teknik
Teknik	Jenis Operasi	Efek Visual	Kapan Digunakan
Image Blending	Kombinasi dua citra	Menggabungkan visual	Overlay dan efek visual
Image Negative	Pembalikan intensitas	Warna terbalik	Analisis detail tertentu
Logaritmik	Kompresi intensitas	Area gelap lebih jelas	Citra gelap
Gamma	Koreksi intensitas	Terang atau gelap	Koreksi pencahayaan
Studi Kasus 1
Foto malam hari yang terlalu gelap dapat diperbaiki menggunakan transformasi gamma dengan nilai γ < 1 atau transformasi logaritmik. Kedua teknik mampu meningkatkan visibilitas detail pada area gelap.
Studi Kasus 3
Untuk menggabungkan foto dan tekstur hujan, teknik yang paling tepat adalah image blending. Perubahan bobot akan menentukan dominasi masing-masing citra pada hasil akhir.
Refleksi Pribadi
Teknik yang paling mudah dipahami adalah image negative karena hanya menggunakan operasi pengurangan nilai piksel. Teknik yang paling sulit dianalisis adalah transformasi gamma karena efek visualnya berubah sesuai nilai gamma yang digunakan.
Melalui praktikum ini dipahami bahwa perubahan nilai piksel secara matematis dapat menghasilkan perubahan visual yang signifikan pada citra digital.
Kesimpulan
Setiap teknik manipulasi citra memiliki tujuan yang berbeda. Image blending digunakan untuk menggabungkan citra, image negative untuk membalik intensitas, transformasi logaritmik untuk meningkatkan detail area gelap, dan transformasi gamma untuk koreksi pencahayaan. Pemilihan teknik yang tepat sangat bergantung pada kondisi citra dan tujuan pengolahan yang diinginkan.
