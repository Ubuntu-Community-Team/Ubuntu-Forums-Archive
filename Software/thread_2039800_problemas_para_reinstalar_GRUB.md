---
title: "problemas para reinstalar GRUB"
date: 2012-08-09
forum: Software
---

### Post by drazhe on 2012-08-09
Hola, estoy teniendo problemas para reinstalar grub siguiendo los suiguientes pasos... 

> ....
**sudo fdisk -l**

**sudo mount /dev/sda5 /mnt** *(el 5 se reemplaza con el número de la particion del Linux)*

**sudo grub-install --root-directory=/mnt/ /dev/sda**



Al llegar al último paso, donde siempre me daba el mensaje de *no errores*, ahora me tira lo siguiente

> 
/usr/sbin/grub-setup: warn: Su área de empotrado es inusualmente pequeña. core.img no cabrá en ella..
/usr/sbin/grub-setup: warn: No es posible incrustar. GRUB sólo puede instalarse en esta configuración usando listas de bloques. Sin embargo, éstas NO SON FIABLES y su uso está desaconsejado..
/usr/sbin/grub-setup: error: Si realmente quiere usar listas de bloques, use --force.
ubuntu@ubuntu:~$ 


Hay alguna manera de reparar esto sin tener que reinstalar todo desde el principio? 
desde ya muchas gracias.... 


PD:
agrego la lista que me da al poner **sudo fdisk -l** por si hace falta... 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x26662665

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       43728   351241286+   7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2           43728       60802   137143297    5  Extendida
La partición 2 no termina en un límite de cilindro.
/dev/sda5           43728       60103   131531776   83  Linux
/dev/sda6           60103       60802     5610496   82  Linux swap / Solaris


---

### Post by rojojuan on 2012-08-09
Fijate si te sirve esta página.

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by gmunioz on 2012-08-11
Esto es lo que uso y me sirve:

sudo su
mkdir /mnt/disco
mount /dev/sda5 /mnt/disco
mount --bind /dev/ /mnt/disco/dev
mount --bind /sys/ /mnt/disco/sys
mount --bind /proc/ /mnt/disco/proc
chroot /mnt/disco
grub-install --root-directory=/mnt/disco /dev/sda
grub-install --recheck /dev/sda
update-grub

---

### Post by drazhe on 2012-08-19
Hola, al final no me sirvió ninguno de los métodos que me indicaron y terminé reinstalando todo.. y cambiando un poco los tamaños de las particiones y todo parece haberse solucionado ya que no vuelve a tirarme los mensajes de que las particiones no terminan en el final de un cilindro como si lo hacía antes... 
Por mi parte puedo dar de por cerrado éste hilo, pero si algún administrador piensa que no lo está, me disculpa y lo vuelve a abrir... 

Desde ya gracias por la atención y la ayuda que me dieron...

---

