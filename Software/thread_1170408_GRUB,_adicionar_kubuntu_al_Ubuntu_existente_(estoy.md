---
title: "GRUB, adicionar kubuntu al Ubuntu existente (estoy mareado!!)"
date: 2009-05-26
forum: Software
---

### Post by dhcancelo on 2009-05-26
Buenas.... Una consulta.
Tengo distribuido mi disco de esta forma:

Disco /dev/sda: 160.0 GB, 160041885696 bytes 
255 cabezas, 63 sectores/pista, 19457 cilindros 
Unidades = cilindros de 16065 * 512 = 8225280 bytes 
Identificador de disco: 0x0ba40ba4 

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema 
/dev/sda1   *           1        6311    50693076    7  HPFS/NTFS 
/dev/sda2            6312        7553     9976365    7  HPFS/NTFS 
/dev/sda3            7554        7617      514080   83  Linux 
/dev/sda4            7618       19457    95104800    5  Extendida 
/dev/sda5            7618        9529    15358108+  83  Linux 
/dev/sda6           11549       11930     3068383+  82  Linux swap / Solaris 
/dev/sda7           11931       19457    60460596   83  Linux 
/dev/sda8            9530       11548    16217586   83  Linux 

Las entradas de la tabla de particiones no están en el orden del disco 

En sda3 tengo el boot donde se encuentra el grub de ubuntu, la / esta en sda5 y el home en sda7.
Cree una particion nueva en sda8 con formato ext4 para probar kubuntu. Instale este ultimo con su boot dentro de la / y comparti la swap con la de HH y tambien la home creando un usuario con nombre distinto al de ubuntu HH.

El problema es que al iniciar el menu del grub me mostraba solo el "vosta" (que todavia esta por la garantia) y el nuevo kubuntu.
Recupere el grub con super grub disk y ahora me quedo como estaba originalmente, no tiene el kubuntu. Entonces copie las entradas del menu.lst del kubuntu y las agregue al final del menu.lst del ubuntu que esta en sda3.

Al inicio me muestra el ubuntu y el nuevo kubuntu, pero al seleccionarlo este ultimo me sale:
ERROR 15 File not found

Estos son los menu del menu.lst

Del Ubuntu en sda3/boot/grub:

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=919374dd-7233-4e13-8c0d-266f360727eb ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=919374dd-7233-4e13-8c0d-266f360727eb ro single
initrd		/initrd.img-2.6.24-23-generic

El del Kubuntu en sda8/boot/grub (ext4):

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		86500bfb-e481-4050-9835-b94fb56a4706
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=86500bfb-e481-4050-9835-b94fb56a4706 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		86500bfb-e481-4050-9835-b94fb56a4706
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=86500bfb-e481-4050-9835-b94fb56a4706 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

Estas lineas las agregue debejo de las primeras. Los UUID estan bien! Solo les agregue a las nuevas lineas del kubuntu esto que no figuraba, no se si es necesario.. 
root		(hd0,7)

Bueno... creo que no me falta ningun dato... si alguien tiene idea, porque ya no se que probar...
Muchas gracias.
Saludos.
Diego.

---

### Post by staar on 2009-05-26
esta línea 'uuid 86500bfb-e481-4050-9835-b94fb56a4706' cumple la misma función que la que agregaste 'root  (0,7)', asi que no era necesario...

en lo demás, no logro ver ningún error...

saludos

---

### Post by dhcancelo on 2009-05-26
> **staar said:**
> esta línea 'uuid 86500bfb-e481-4050-9835-b94fb56a4706' cumple la misma función que la que agregaste 'root  (0,7)', asi que no era necesario...

en lo demás, no logro ver ningún error...

saludos

me imaginaba que era mas o menos asi.
que raro.... ya no se que hacer...
gracias igual.
saludos.

---

### Post by staar on 2009-05-26
probá reinstalando grub a mano, quizas el SGD no lo reparó bien, desde ubuntu:
```
sudo grub
``` se te abre el intérprete de comandos de grub
```
find /boot/grub/stage1
``` te devuelve el numero de partición donde está la stage1, en tu caso van a salir dos particiones, elegi la partición del /boot de ubuntu
```
root (hdX,Y)
``` reemplazando (hdX,Y) por lo que te dió en el paso anterior
```
setup (hd0)
``` en esta parte va solo el número de disco, no la partición
```
exit
```
por las dudas, tirate un ```
sudo update-grub
```

saludos

---

### Post by dhcancelo on 2009-05-26
ok. cuando llego a casa lo pruebo... despues te cuento!!!
gracias nuevamente.

---

### Post by dhcancelo on 2009-05-26
> **staar said:**
> probá reinstalando grub a mano, quizas el SGD no lo reparó bien, desde ubuntu:
```
sudo grub
``` se te abre el intérprete de comandos de grub
```
find /boot/grub/stage1
``` te devuelve el numero de partición donde está la stage1, en tu caso van a salir dos particiones, elegi la partición del /boot de ubuntu
```
root (hdX,Y)
``` reemplazando (hdX,Y) por lo que te dió en el paso anterior
```
setup (hd0)
``` en esta parte va solo el número de disco, no la partición
```
exit
```
por las dudas, tirate un ```
sudo update-grub
```

saludos

mira:
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,3) #(es donde esta el /boot de ubutnu)
root (hd0,3)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> exit

wex@wex-laptop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-23-generic
Found kernel: /vmlinuz-2.6.24-22-generic
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

El update solo tomo los del ubuntu, no los del nuevo kubuntu.

---

### Post by staar on 2009-05-26
perdón, pero esto ```
find /boot/grub/stage1
``` tendría que haber sido así ```
find /grub/stage1
``` ya que tenés el /boot separado, perdón, my bad...

saludos

---

### Post by dhcancelo on 2009-05-27
lo que hice fue reinstalar kubuntu en sda8 con su boot dentro de la raiz. Monte el /boot (sda3) de ubuntu (sda5), copie las lineas del menu.lst y las agregue al nuevo menu del grub de kubuntu. 
Ahora andan los dos.
¿No andaria porque al usar el grub de ubuntu que estaba en sda3 en formato ext3 tenia que leer sobre una particion formato ext4 (kubuntu)?
No se mucho del tema... pero bue... se me ocurrio!
Muchas gracias por todo.
Saludos.

---

### Post by staar on 2009-05-27
bueno, me alegra que lo hayas solucionado...

ahora me doy cuenta del problema, el ubuntu que tenés es hardy (lo aclaraste en el primer post, pero se me pasó) y el grub de esta versión no soporta ext4, recién el grub de jaunty tiene el parche para soportar ese FS...

saludos

---

