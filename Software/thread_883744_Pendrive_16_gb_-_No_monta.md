---
title: "Pendrive 16 gb - No monta"
date: 2008-08-08
forum: Software
---

### Post by jclevien on 2008-08-08
Buenos dias,

Queria comentarles que me compre un pendrive de 16 gb, con la intencion de almacenar maquinas virtuales dentro del mismo (archivos de mas de 2 GB). Como por defecto viene formateado en FAT32, quise convertirlo a NTFS para compatibilizar Windows y Linux, para mi sorpresa el pendrive lo detecta solo el Windows y el Linux directamente ni lo reconoce.

Estoy trabajando con Ubuntu Hardy y Gutsy en otra laptop (EEEPC).

Lo raro es que en un momento el Linux lo detectaba, y ahora directamente no lo hace, pero Windows si lo detecta siempre.

Probe formatear de nuevo a FAT32, usar el TestDisk para Windows, y nada, no hay caso.

Habra algun driver para Linux que me este faltando para que lo detecte?


Muchas gracias por su respuesta.


Juan

---

### Post by [P]oli on 2008-08-08
Holaa, acá encontré esto, capaz te sirve (si el pen-drive sigue siendo NTFS)
[http://www.cristalab.com/tips/26881/montar-escribir-y-leer-particiones-ntfs-desde-ubuntu.html](http://www.cristalab.com/tips/26881/montar-escribir-y-leer-particiones-ntfs-desde-ubuntu.html)
Ojalá te sirva ;)

---

### Post by pol666 on 2008-08-08
ubuntu ya viene con ntfs-3g :\

---

### Post by undiaperfecto on 2008-08-14
a mi me pasa exactamente lo mismo, pero con una memory stick de 4gb
probe con un lector de tarjetas y nada
probe conectando directamente el movil y me la detecta, pero no lee ni escribe

[[IMG]http://img167.imageshack.us/img167/7277/memoryfailledui4.th.png[/IMG]](http://img167.imageshack.us/my.php?image=memoryfailledui4.png)

---

### Post by pol666 on 2008-08-14
hace un fdisk -l y fijate como se llama el dispositivo 

y despues montalo


sudo mount -t *formato* /dev/**sxx** /media/disk

formato: Pone en que esta formateado
sxx: Pone lo que te diga el fdisk, osea sdb, sda1 o lo que sea, me imagino que te lo marca como sdb

---

