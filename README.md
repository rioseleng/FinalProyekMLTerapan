# FinalProyekMLTerapan - Rio Rezky Seleng

## Project Overview
Perkembangan era digital yang sangat massive saat ini menuntuk beberapa sektor untuk beradaptasi dan memanfaatkan teknologi. Salah satu bidang yang terdampak adalah pendidikan. Pendidikan online menjadi semakin populer belakangan ini, khususnya pendidikan berbasis *online course*. Coursera adalah salah satu platform yang terkenal yang menawarkan ribuan kursus yang disediakan oleh beberpaa universitas maupun organisasi ternama di seluruh dunia. Meskipun memiliki banyak pilihan, pengguna sering kesulitan menemukan kursus yang sesuai dengan kebutuhan dan minat mereka. Proyek ini bertujuan untuk mengembangkan sistem rekomendasi kursus di Coursera menggunakan teknik machine learning. Sistem ini akan membantu pengguna menemukan kursus yang relevan berdasarkan preferensi dan minat mereka, sehingga dapat meningkatkan pengalama pengguna dan efisiensi waktu dalam mencari kursus yang relevan. Dengan memanfaatkan data list course yang ada, sistem ini diharapkan dapat memberikan rekomendsai yang lebih akuran dan bermanfaat dan mendudukng pengembangan keterampilan dan karir pengguna. Proyek ini dianggap penting untuk diinisiasi karena dapat meningkatkan kepuasan dan retensi pengguana, serta membantu coursera dalam menyediakan kursus yang lebih dipersonalisasi dan efektif bagi semua penggunanya.
## Business Understanding
### Problem Statement
Ketersediaan ribuan pilihan kursus pada platform coursera dapat menjadi suatu tantangan pada user ketika ingin menemukan kursus yang paling relevan. Pengguna sering merasa kewalahan dengan banyaknya pilihan dan kesulitan dalam menemukan kursus yang sesuai dengan kebutuhan dan minat mereka. Hal ini dapat mengakibatkan kurangnya efisiensi waktu dalam pencarian kursus yang relevan, menurunkan pengalaman pengguna, serta mengakibatkan rendahnya keterlibatan dan retensi pengguna di platform coursera. Project ini dibatasi hanya pada course yang judulnya menggunakan bahasa inggris
### Goals
Proyek memiliki tujuan untuk mengembangkan sitem rekomendasi kursus yang efektif di coursera dengan memanfaatkan teknik machine learning. Tujuan utama dari sistem ini adalah untuk membantu pengguna menemukan kursus yang relevan berdasarkan preferensi dan minat mereka, sehingga dapat meningkatkan pengalaman pengguna dan efisiensi waktu dalam mencari kursus yang sesuai. Dengan menggunakan data list course yang ada, sistem ini diharapkan dapat memberikan rekomendasi yang lebih akurat dan bermanfaat, mendukung pengembangan keterampilan dan karir pengguna. Selain itu, proyek ini juga bertujuan untuk meningkatkan kepuasan dan retensi pengguna, serta membantu Coursera dalam menyediakan kursus yang lebih dipersonalisasi dan efektif bagi semua penggunanya.
## Data Understanding
Data yang digunakan pada proyek ini berjumlah 891 records. Data ini memiliki 6 column identik yang digunakan untuk menyimpan informasi yang dapat digunakan untuk membuat sebuah sistem rekomendasi.\
Data ini diakses dan diunduh melalui webiste penyedia data, yaitu [Kaggle](https://www.kaggle.com/code/sinya1398/content-based-course-recommendation). Penjelasan tentang 6 variabel yang terdapat pada dataset adalah sebagai berikut:
 - course_title: Variable ini menggunakan tipe data object dan digunakan untuk menyimpan title dari kursus yang tersedia di platform coursera
 - course_organization: Object adalah tipe data yang digunakan pada variabel ini dan variabel ini digunakan untuk menyimpan informasi tentang ornganisasi yang membuat atau menyelenggarakan kursus
 - course_Certificate_type: Variabel ini digunakan untuk menyimpan jenis sertifikasi yang terdapat pada kursus tersebut. Data type dari variabel ini adalah object.
 - course_rating: Menjadi salah satu variabel yang menggunakan tipe data float pada dataset ini, variabel ini digunakan untuk menyimpan jumlah rating yang diberikan oleh pengguna pada kursus tersebut
 - course_difficulty: Menggunakan tipe data object, variabel ini digunakan untuk menyimpan tingkat kesulitan atau level dari kursus tersebut.
 - course_students_enrolled: Tipe data object digunakan pada variabel ini agar dapat mengsubtitusi satuan ribu dengan huruf "K". Variabel ini digunakan untuk menyimpan data jumlah pengguna yang telah mendaftar pada kursus tersebut.
## Data Preparation
 1. **Menghapus *unnamed* column**\
 Pada tahapan ini, saya menghapus column `unnamed` yang tidak diketahui tujuannya untuk menyimpan data apa. Column ini dihapus karena ditakutkan dapat menggangu performa model ketika dia diikutkan pada proses training model dan juga dapat membingungkan data scientist atau machine learning engineer pada saat melakukan pemodelan atau dengan kata lain akan lebih mudah bagi seseorang untuk meninterpretasikan sebuah data apabila setiap column diketahui tujuannya untuk apa. Lebih jauh lagi, proses ini dilakukan untuk mengurangi kebisingan data, mengurangi dimensionalitas, dan mempercepat proses komputasi.
 2. **Pengecekan Missing Value**\
 Pada tahapan ini dilakukan dengan memanfaatkan method `isnull` dan `sum` untuk mengidentifikasi column mana yang memiliki missing value. Tahapan ini dilakukan untuk menjaga kualitas data, mencegah bias, dan dapat meningkatkan performa model.
 3. **Mengecek Duplikasi data**\
 Melakukan pengecekan duplikasi data dapat digunakan dengan memanfaatkan method `duplicated` yang digabungkan dengan `sum`. Hal ini dilakukan untuk memastikan bahwa tidak ada data yang redundan yang dapat mempengaruhi kinerja model dan juga memastikan konsistensi pada data.
 4. **Menghapus baris yang memiliki `course_title` tidak berbahasa inggris**\
 Pada percobaan ini, saya menggunakan library `langdetect`. Library tersebut membantu saya untuk mendeteksi baris mana saja yang menggunakan bahasa inggris pada column `course_title`. Hal ini dilakukan untuk menyesuaikan batasan yang telah disebutkan pada problem statement.
 
## Modeling and Result
Pada pemodelan kali ini, saya hanya menggunakan model **Content-Based Filtering** \
Content-based filtering adalah teknik rekomendasi yang menggunakan informasi tentang item yang akan direkomendasikan serta preferensi pengguna untuk menghasilkan rekomendasi. Dalam konteks model rekomendasi kursus yang telah kita buat, model ini menganalisis berbagai atribut judul kursus. Beberapa tahap yang dilakukan untuk membuat sistem rekomendasi dengan pendekatan _content-based filtering_ adalah TF-IDF Vectorizer, _cosine similarity_, dan pengujian sistem rekomendasi.

- TF-IDF Vectorizer

  TF-IDF Vectorizer akan melakukan transformasi teks judul course menjadi bentuk angka berupa matriks.

- Cosine Similarity

  Cosine similarity digunakan untuk menghitung tingkat kesamaan antara dua data judul kursus dengan mengukur sudut antara kedua data tersebut. Teknik ini menghitung tingkat kesamaan dengan menggunakan sudut antara data judul kursus yang dianalisis. Hasil perhitungan ini akan memberikan nilai yang menunjukkan tingkat kesamaan antara dua judul kursus, dimana nilai yang mendekati 1 menunjukkan tingkat kesamaan yang tinggi, dan nilai yang mendekati 0 menunjukkan tingkat kesamaan yang rendah.

- Hasil _Top-N Recommendation_

  Setelah data judul kursus dikonversi menjadi matriks dengan menggunakan TF-IDF Vectorizer, dan tingkat kesamaan antar judul kursus ditentukan dengan menggunakan cosine similarity, selanjutnya dilakukan pengujian terhadap sistem rekomendasi yang menggunakan pendekatan content-based filtering recommendation. Hasil dari pemodelan yang saya buat adalah sebagai berikut:
  Test 1: A Crash Course in Data Science. Top 5 Course yang direkomendasikan oleh sistem adalah:
  |course_title|course_organization|course_difficulty|
  | --------- | ---------- |----------|
  |1. Crash Course on Python| Google | Beginner|
  
  Kelebihan dan kekurangan dari content based filtering adalah sebagai berikut
  |Kelebihan|Kekurangan|
  | -------- | ---------- |
  |1. Dapat digeneralisasi karena data pengguna lain tidak diperlukan untuk merekomendasikan sesuatu kepada pengguna tertentu|1. Sistem ini bergantung pada ketersediaan dan kualitas fitur konten. Jika atribut atau metadata tidak lengkap atau tidak akurat, rekomendasi yang dihasilkan bisa jadi kurang relevan.|
  |2.Pemfilteran berbasis konten dapat memberikan rekomendasi yang sangat dipersonalisasi karena rekomendasi didasarkan pada preferensi spesifik pengguna.|2. Model dapat merekomendasikan item baru berdasarkan minat pengguna saat ini. Oleh karena itu, menemukan dan memperluas rekomendasi ke item lain yang berbeda preferensi, yang mungkin menarik bagi pengguna tidak mungkin dilakukan.|

## Evaluation
