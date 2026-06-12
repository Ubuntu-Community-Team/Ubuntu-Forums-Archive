---
title: "Problemas para instalar ubuntu 10.4"
date: 2010-04-29
forum: Software
---

### Post by loloman on 2010-04-29
Algo curioso es que al tratar de instalar ubuntu 10.4 no me detecta el HD (sata II 160gb) pero al entral al modo live-CD veo las particiones sin problemas y gparted las detecta, pero el instalador no ???? nunca antes he tenido problemas para instalarlo pero mi disco ide secundario (250 gb) si lo detecta pero ally no lo puedo instalar

Posible sopechoso: Grub he tenido problemas con el y no lo puedo sacar, esta instalado en el disco Sata con el que tengo problemas

Mi PC:
MSI K8TNeo2 Atlhon 64 3200+ 1,5GB DDR Gforce6600gt HD IDE 250gb sata II 160gb

La configuracion de mis particiones es:
HD 250GB Ide Primario master, Particion primaria 
(windows XP C 60GB ntfs)(D 80gb ntfs)(E 110bg)

Sata II 160 En la controladora Raid (solo asi lo detecta mi mainboard) 
( / ext4 Ubuntu 20gb)(1gb swatp)(f 50bg ntfs)(g 89GB ntfs)

---

### Post by loloman on 2010-04-30
Otro detalle, se puede instalar el ubuntu 9.04 y anteriores pero el 9.10 tiene el mismo problemas... :confused:

No logro sacar el grub, alguien sabe de algun metodo para borrar el mbr desde un live-cd ?

---

### Post by loloman on 2010-04-30
por si no se entiende ...

Se pueden ver las particiones sin problema :confused::confused::confused:

[[IMG]http://img717.imageshack.us/img717/6168/pantallazodevsdegparted.png[/IMG]](http://img717.imageshack.us/i/pantallazodevsdegparted.png/)

Pero al instalar no las muestra :confused::confused::confused:

[[IMG]http://img72.imageshack.us/img72/8507/pantallazoinstalar.png[/IMG]](http://img72.imageshack.us/i/pantallazoinstalar.png/)

Creo que de ultima solo me queda Actualizar desde 9.04

---

