---
title: "VNC Viewer configuración"
date: 2009-07-16
forum: Software
---

### Post by Josecanalla on 2009-07-16
Hola, tengo una Notebook con Ubuntu 9.04 y configuré para en "Preferencias de escritorio remoto": "Permitir que otros usuarios vean mi escritorio" y "Permitir que otros usuarios manejen mi escritorio", activado. 

Esta notebook se conecta a internet por wi-fi mediante un router que tengo en mi casa, el mismo router del cual sale un cable a la PC de escritorio, con Windows XP, desde la cual quiero controlar el escritorio de la notebook. Me instalé el VNC Viewer en esta PC de escritorio que les comento, y cuando intento conectar poniendo la IP:5900 (es el puerto que utiliza el programa), por ejemplo, en mi caso: 192.168.1.21 (la IP la averigué tecleando ifconfig en la terminal, y en wlan me salió esa dirección IP). 

La cuestión que cuando pongo 192.168.1.21:5900 y pongo Connetc, me sale FAILED TO CONNECT TO SERVER!

¿Qué puedo hacer? ¿Puede ser que tenga que abrir el puerto 5900 en el router? En ese caso, ¿debo abrirlo para la PC de IP .21 (Notebook) o para la PC de IP .4 (escritorio)?

Ayuda!

---

### Post by jpmorelli on 2009-07-16
Si las dos PC están en la misma red ( o conectados al mismo router ya sea por wlan o por lan ) no necesitás abrir el puerto en el router.
Fijate porque o en tu XP o en tu notebook tenés puesto algun firewall que no te permite pasar por el puerto 5900.

---

### Post by Josecanalla on 2009-07-16
En la que tiene XP, tengo el firewall de Windows, y automáticamente al instalar el VNWiever se abren los puertos 5800 y 5900... Y en la que tiene Ubuntu no toqué nada. ¿Cómo puedo verificar que los puertos estén abiertos?

---

