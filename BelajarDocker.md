# Belajar Docker

## Command di Docker
1. `docker version`

  untuk cek versi docker yang di pakai saat ini

2. `docker info`

   untuk melihat secara rinci isi dari docker yang ada, bisa melihat berapa container dan image yang aktif, cpu usage, dll

3. `docker - -help`

   melihat command apa aja yang ada di docker

4. `docker container ls`

   untuk melihat container mana yang sedang aktif

5. `docker container stop idContainer`

   Untuk menghentikan container yang sedang aktif, id container di dapat dari perintah `docker container ls`

6. `docker container ls -a`

   untuk melihat semua log container yang ada (baik aktif atau non aktif)

7. `docker container run image`

   selalu menjalankan new container

8. `docker container start idContainer/nameContainer`

   menjalankan existing container yang ada, jadi jika container sudah d stop, maka bisa dijalankan kembali dengan perintah ini, untuk melihat container mana aja yang pernah di aktifkan, bisa melihat di log container yang pernah di aktifkan dengan perintah `docker container ls -a`

9. `docker container logs namaContainer`

   untuk melihat log dari suatu container

10. `docker container top namaContainer`

   melihat proses yang jalan di spesifik container

   untuk melihat proses yang jalan di suatu container

11. `docker container rm idContainer1, idContainer2, dll`

    menghapus container yang aktif, bisa multiple container yang kita hapus. tinggal di masukin id ne dan dipisahkan dengan spasi

    NOTE:

    Untuk menhapus suatu container, kita harus menghentikan (stop) container yang sedang jalan

12. `docker container rm -f idContainer`

    untuk menghapus container secara paksa container yang sedang aktif atau tidak aktif. command ini jika ada container yang aktif atau jalan, maka akan tetap d hapus

13. `docker container run --publish 8080:80 --name webhost -d nginx:1.11 nginx -T`

    menjalankan container dari image nginx dengan port 8080 di local, dan di lempar ke container dengan port 80

    membuat container dengan nama container: webhost

    menjalankan spesifik versi dari 'nginx' yaitu versi 1.11

    'nginx -T' mengganti CMD run on start

14. `ps aux`

    untuk melihat semua proses yang sedang jalan di device kita

15. `--detach or --detached or -d`

    untuk menjalankan aplikasi di background

16. `-p`

    Membuka port di docker agar dijalankan dengan port tertentu

17. `--name`

    memberikan nama pada suatu container

18. `-e`

    memberikan envairoment variabel pada suatu container

19. `docker container inspect`

    untuk melihat detail config salah satu container

20. `docker container stats`

    untuk melihat performance status semua container

21. `docker container run -it --name namaContainer imageContainer bash`

    menjalankan new container secara interactively (masuk ke dalam containernya) yang di jalankan dalam bash

22. `docker container exec -it namaContainer bash`

    menjalankan container secara interactively (masuk ke containernya) yang dijalankan dalam bash

23. `docker pull namaImage`

    untuk mendownload docker image dari docker hub

24. `docker image ls`

    untuk melihat semua image yang sudah terinstal di laptop atau device kita

25. `docker rmi namaImage`

    untuk menghapus spesifik nama Image yang sudah terinstal di laptop kita

26. `-it`

    menjalankan secara interaktif suatu image di container (masuk ke dalam container imagenya)

27. `bash`

    media untuk menjalankan container image, jadi container dijalankan di atas bash

28. `sh`

    media untuk menjalankan container image, jadi container dijalankan di atas sh (shell). alternatif pengganti bash

29. `docker container port namaContainer/Id`

    untuk melihat port yang jalan atau yang di pakai dari suatu container

30. `docker network ls`

    untuk melihat informasi semua netwok yang pernah jalan di engine docker

31. `docker network inspect nameDriver/idNetwork`

    untuk melihat informasi lengkap config dari suatu network, bisa melihat network tersebut terhubung dengan container mana saja

32. `docker network create nameNetwork`

    untuk membuat new virtual network. Secara default akan di arahkan ke driver bridge

33. `docker network create nameNetwork --driver nameDriver`

    untuk membuat new virtual network  dengan spesifik mengarahkan ke driver tertentu

34. `docker network connect nameContainer nameNetwork` 

    Menghungkan semua container ke sebuah network. Membuat NIC (network interface controller) di suatu existing virtual netwok

35. `docker network diconnect`

    untuk meng diskonek (stop) network dari suatu container

36. `docker container run -d --name new_nginx --network my_app_net nginx`

    menjalankan container baru dengan nama new_nginx, dihungkan dengan network my_app_net, dengan image nginx

37. `docker container run -d --net dude --net-alias search elasticsearch:2`

38. `docker container run --rm --net dude alpine nslookup search`

39. `docker container run --rm --net dude centos curl -s search:9200`

40. `docker image ls`

    untuk melihat ada image apa saja yang sudah terinstall

41. `docker pull nameImage`

    untuk mendownload docker image dari docker hub

42. `docker history nginx:latest`

    untuk melihat history perubaha dari layer suatu image (nginx)

43. `docker inspect image`

    return JSON meta data dari suatu image

44. `docker image tag namaTag:versi`

    meregistrasikan satu atau lebih tags ke suatu image (default latest)

45. `docker pull namaImage:namaTag`

    untuk mendownload nama image + di ikukti nama Tag nya

46. `docker image push namaTag`

    upload perubahan layer ke sebuah image registry (default ke hub)

47. `docker login`

    untuk login akses ke account docker, untuk melakukan push ke docker hub, kita wajib login dan setelah selesai, wajib untuk logout juga

48. `docker logout`

    untuk logout dari akun docker hub

49. `docker image build -t namaImage .`

    untuk membuat suatu image dari docker file, dengan nama image nginx-with-html (masuk ke directory Dockerfile dlo)

50. `docker volume ls`

    melihat semua volume yang ada di engine

51. `-v lokasiFolderVolume(/var/lib/mysql)`

    contoh: `docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD = true -v mysql-db:/var/lib/mysql mysql`

    memberi volume saat container akan di jalankan bersama dengan `docker run`

52. docker volume create 

    contoh menjalankan container nginx dengan custom valume letak file html

    `2`

    ​



**Image vs Container**

1. Image

   Image jalan di atas container

   berisi aplikasi yang siap untuk dijalankan. contoh image adalah image nginx, image ubuntu, dll. 

   Image bisa di pasang di dalam container, kita juga bisa membuat image baru dari image yang lama. misalnya kita buat image ubuntu yang sudah terinstal nginx, mysql, php , dll

2. Container

   Suatu wadah yang bisa untuk menjalankan suatu image, dalam container kita bisa menjalankan image.

   Kita bisa menjalankan banyak image dalam satu container



**Docker Hub**

1. Sebuah package manager yang ada di docker
2. berisi image-image docker
3. kita bisa mengapload image yang kita buat dalam docker-hub



**Membuat suatu container  (contoh nginx)**

1. Jalankan perintah berikut untuk membuat container yang berisi image nginx, dan dijalankan pada port 80

`docker container run --publish 80:80 nginx`

- Download image 'nginx' dari docker hub

- Jalankan new container dari image 'nginx'

- Membuka port 80 di host IP (karna local jd localhost)

- Menjalankan host container dengan port 80

- Perintah di atas hanya jalan di backgorund, ketika pencet CTR + C, maka caintainer nginx kita akan mati, untuk menjalankan secara terus menerus (aktif) container image 'nginx' kita, maka perlu di tambahkan command '- -detach'. 

  Maka perintahnya akan menjadi seperti berikut:

  `docker container run --publish 80:80 --detach  nginx`

  ​

2. Membuat container dari image 'nginx' dengan custom nama container dengan nama webhost

   `docker container run --publish 80:80 --detach  --name webhost nginx` 

   contoh docker menjalankan mongo db (cari d docker hub jika lokal tidak tersedia), dengan name container mongo

   `docker run --name mongo -d mongo`



Yang terjadi jika `docker container run nameContainer/Id` dijalankan (jika casenya nginx)

1. pertama, akan melihat image di local dan image di cache, jika ada maka akan menjalankan yang di local, namun jika tidak ada (step no 2)
2. Jika local tidak ditemukan, maka akan nembak mencari di image repository (default to docker hub)
3. otomatis akan mendownload latest version dari image tersebut
4. Membuat (create) container baru dari image yang di download atau d temukan dan persiapan untuk dijalankan
5. Memberikan virtual IP di provate network pada docker engine (docker yg terinstal di laptop/server)
6. membuka port 80 di host dan mengembalikan ke port 80 di container yang di create
7. Menjalankan container dari CMD command yang ada di docker file dalem image



Container bukan merupakan mini VM (virtual machine), karena

1. container hanya menjalankan suatu proses
2. keterbatasan akses resource yang dapat di akses
3. exit (keluar) ketika proses di hentikan



**IMAGE**

1. image adalah suatu binary dan dependency
2. Image bisa berisi small atau bagian kecil dari aplikasi kita (misal image hanya berisi nginx, ubuntu, dll)
3. Image juga bisa berisi kumpulan image yang sudah disatukan menjadi 1 image, 1 image bisa berisi macem-macem, contoh: image ubuntu yang sudah d install apache, php, mysql, dll

**Membuat Image sendiri**

1. Membuat Dockerfiles

   dockerfiles merupakan bagian penting yang berisi scripte code untuk yang di baca saat image docker akan di build atau d buat

2. pilih beberapa part dockerfile image yang akan di tambahkan pada image docker yang akan kita buat

3. Beri nama tag pada image docker kita

4. push docker image kita ke dockerhub (wajib login dlo)

5. remove (hapus) image di local cache kita, dan jalanin image yang kita buat dari dockerhub

List Image yang Penting dan sering di pakai

1. alpine

   image berbasis linux yang ukuranya sangat kecil, hanya 5mb. bisa digunakan pengganti ubuntu

2. nginx

   image web server nginx

3. httpd

   image web server untuk apache

4. ubuntu

   image untuk ubuntu OS

5. mysql

   image untuk mysql database




**Docker Volume**

1. Menandai beberapa folder dalam container menjadi volume
2. Volume bisa di mapping ke folder di sistem host, sehingga isinya bisa langsung diakses walaupun container sedang mati
3. Volume juga bisa dipakai  untuk menyelamatkan file dalam container agar tidak terhapus saat container di hapus.
4. Volume kita bisa berbagi file dan folder dengan container lain. misalnya kita ingin membuat replikasi atau clustering dimana file-file aplikasi harus bisa diakses dari semua container/instance





note

password root = eiy4ci4uoy3ohNgahw6Iewiephaihoox

