---
title: "Ayuda con backup"
date: 2011-12-20
forum: Software
---

### Post by nicoyaros on 2011-12-20
Quiero hacer un backup de un directorio en ubuntu server 11 a un disco externo.

Basicamente, tengo un carpeta /home/files que adentro tiene multiples directorios y subdirectorios con muchos archivos.
  

Lo que necesito hacer es un backup semanal FULL los  días domingo, y que durante todos los días, hacer el incremental de lo  que se modificó.


Al domingo siguiente, cuando se hace de nuevo el FULL, debería borrarse todo lo anterior. 
  

La idea es que pueda seleccionar que directorios excluir y que tipos de archivo (.mp3, .mpg, .avi, etc) excluir.


Por favor si alguien tiene un programa o un script que haga esto, por favor pasarlo.
  

Gracias!

---

### Post by shubham1 on 2011-12-20
> **nicoyaros said:**
> Quiero hacer un backup de un directorio en ubuntu server 11 a un disco externo.

Basicamente, tengo un carpeta /home/files que adentro tiene multiples directorios y subdirectorios con muchos archivos.
  

Lo que necesito hacer es un backup semanal FULL los  días domingo, y que durante todos los días, hacer el incremental de lo  que se modificó.


Al domingo siguiente, cuando se hace de nuevo el FULL, debería borrarse todo lo anterior. 
  

La idea es que pueda seleccionar que directorios excluir y que tipos de archivo (.mp3, .mpg, .avi, etc) excluir.


Por favor si alguien tiene un programa o un script que haga esto, por favor pasarlo.
  

Gracias!
hola
 Creo que deberías ver esto rsync
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
 también se puede ver este
 [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)
 ver en este enlace que contiene información útil
 [https://help.ubuntu.com/11.04/serverguide/C/backups.html](https://help.ubuntu.com/11.04/serverguide/C/backups.html)

---

### Post by nicoyaros on 2011-12-20
Muchas gracias!
Estoy probando el rsync, si alguien tiene algun ejemplo de un backup incremental, otro full y que lo comprima por favor pasenmelo.

Saludos!

---

### Post by alfplayer on 2011-12-21
Te recomiendo investigar primero rdiff-backup y rsnapshot.

---

