---
title: "Problemas con emesene"
date: 2009-07-15
forum: Software
---

### Post by guidito73 on 2009-07-15
Buenas gente!

La verdad que vengo con este problema hace rato... lo habia parcheado un poquito con emesene crazy, pero en fin...

Usando la versión de emesene de repositorios, o la de la pagina oficial, cuando lo arrancó me da este error por la terminal:

> /usr/share/emesene/emesenelib/SignalHandler.py:21: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/usr/share/emesene/emesenelib/Msnobj.py:21: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
If you are reading this, you may want to enable debug
It's the first option in the connection tab in preferences
File /home/guido/.config/emesene1.0/guidito73_gmail_com/custom_emoticons/map does not exist, skipping
The read operation timed out
The read operation timed out
The read operation timed out


Y después de eso, el emesene queda colgado y sin conectarse. Adjunto una screenshot.

Asi que deduzco que tiene que haber algo con Python mal... como dije antes, usando emesene crazy logro conectarme, pero se me cae la conexion, no llegan los mensajes, un desastre: y todo con el mismo error.

Qué puede ser???

[IMG]http://i25.tinypic.com/drcc41.png[/IMG]

---

### Post by Mauro22 on 2009-07-17
Hola!!


Podes crear un archivo vacio llamado "map" como dice el error:

/home/guido/.config/emesene1.0/guidito73_gmail_com/custom_emoticons/map


O podes ir a .config y cambiarle el nombre a la carpeta emesene1.0 para que el programa cree una nueva. Lo unico que perdes son los emoticones y la configuracion..

---

### Post by guidito73 on 2009-07-19
El problema no es ese, sino el error con los archivos .py...

Igual hice lo que dijiste, y el error de 'map' ya no aparece, pero siguen quedando los anteriores... :(

---

