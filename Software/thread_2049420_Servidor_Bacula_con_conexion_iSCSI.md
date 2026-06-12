---
title: "Servidor Bacula con conexion iSCSI"
date: 2012-08-28
forum: Software
---

### Post by ealvaradobsas on 2012-08-28
Bien, estoy armando un servidor Bacula para aproximadamente 200 estaciones de trabajo que ejecutan Windows xp con Ubuntu 12.04
Primero, a modo pruebas/educativo instale un Ubuntu desktop 12.04 y comence el proceso...
Nada facil ya que la primer traba fue que por el lugar en donde lo debo instalar no tengo salida a internet, me llevo varios dias obtener las configuraciones necesarias para poder instalar los paquetes, es una red en donde el proxy utiliza la direccion de correo electronico como nombre de usuario por lo tanto hay una arroba en el mismo
Bien esto ya esta, aunque parciamente, solucionado
Logre instalar bacula, mysql, etc.
Una de las cuestiones es que no se si mysql sera la mejor opcion o deberia utilizar postgre?
El otro tema lo tengo con la conexion iSCSI, para pruebas tengo uns storage iOmega ix12 de 5.7 Tb el que dividi en dos discos iSCSI de 2.7TB cada uno, el storage definitivo sera un IBM SystemStorage DS3512
El drama lo tengo con las conexiones, logre conectarme, formatear y montar pero no lo logro hacer de forma automatica al iniciar el sistema y que quede montados en una ruta fija para luego poder configurar Bacula con este path
Tengo que configurar udev pero ni idea como
y como hago para que los monte al inicio, ahora me tira un error al iniciar el ubuntu y por lo que pude hacer en esa consola aparentemente no levanto la parte de red, ni siquiera me deja iniciar networking solo me da la LP en ifconfig

Gracias

---

