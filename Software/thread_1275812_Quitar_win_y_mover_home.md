---
title: "Quitar win y mover /home"
date: 2009-09-26
forum: Software
---

### Post by sitiomatic on 2009-09-26
Hola 
Tengo intenciones de quitar win de mi maquina y mover /home a la particion que hoy ocupa win.
Sobre lo de mover /home encontre un post muy bien explicado aunque me queda una duda.
Empecemos por el principio, mi maquina es una celeron 500 2ghz con 2 gigas ram, ubuntu 9.04 con kernel 2.6.31. 
1) Alcanza para correr luego win con virtualbox? Necesito solamente usar explorer 7, 8 y outlook ya que me dedico a desarrollo web y debo chequear como quedan las cosas ahi y explorer 7 no me anduvo bien ni con ies4linux ni con el metodo de playonlinux
2) Alguien me pasaria los pasos a seguir desde el principio hasta la movida de /home ? (para mover /home sigo el otro post [http://ubuntuforums.org/showthread.php?t=1265017]("http://ubuntuforums.org/showthread.php?t=1265017") )
3) el otro post para mover home se refiere a ext4 y yo tengo ext3, cuando llega a la parte de editar fstab pone lo siguiente:
> #/dev/sda1             
UUID=aqui la salida de vol_id /home ext4 defaults 0 2

Que deberia poner yo usando ext3?
4) Que debo editar para quitar win de grub?
Gracias a quien pueda responder

---

### Post by gmunioz on 2009-09-26
Hola sit.....:

1- Estimo que para esos programas te sobra.

2- 
a- Desmontas la partición de Windows
b- Instalas gparted 
c- Pulsas Sistema - Administración - Editor de particiones
d- eliminas la particion - creas una nueva - aplicas los cambios

3- #/dev/sda1
UUID=aqui la salida de vol_id /home ext3 defaults 0 1

4- /boot/grub/menu.lst

---

### Post by sitiomatic on 2009-09-26
Gracias.
Anduvo de lujo.

---

