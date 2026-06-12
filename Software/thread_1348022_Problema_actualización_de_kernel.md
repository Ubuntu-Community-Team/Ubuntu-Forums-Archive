---
title: "Problema actualización de kernel"
date: 2009-12-06
forum: Software
---

### Post by RENGOdeDIA on 2009-12-06
Hola, tengo instalado Ubuntu 9.10 en un pendrive, lo instale al poco tiempo que salío KK (fines de octubre 09) con el kernel 2.6.31-14 y anda sin ningún problema.

Al tiempo de eso y al correr el gestor de actualizaciones esta disponible el kernel 2.6.31-15, lo marco para actualizar y lo baja sin problemas, el inconveniente es que cuando lo esta instalando, me dice que no encuentra el /boot/grub/menu.lst y me pregunta si lo quiero crear, y aca el error fue mío porque le dije que si, siguió instalando y me pide reiniciar como siempre. Reinicio pero en el grub sigue apareciendo el kernel 2.6.31-14.

Como andaba bien y yo estaba con poco tiempo lo deje pasar, en la proxima actualizaciòn le digo que no y listo me dije. Dicho y echo, esta semana salio la 2.6.31-16, actualizo y cuando pregunta por menu.lst le digo que no, reinicio pero sigue apareciendo solo el 2.6.31-14.

Tengo instalado el administrador de arranque y ahi me figuran los tres kernels y tengo puesto la opción para que mantenga 4 kernels pero nada.

Aclaro que el 2.6.31-14 anda bien, solo que me gusta tener el sistema lo mas actualizado posible. Otra opción seria borrar las imagenes de kernel viejas pero como las mas nuevas no las probé todavía (no creo que halla problemas pero uno nunca sabe) no me quise arriesgar y quise consultarlo aca primero. Busque pero no encontre algo parecido.

Yo supongo que el error debe ser porque el adm de arranque es para grub y yo tengo el grub2 (1.97 en realidad) pero aca se me quemaron los papeles.

Pido disculpas por lo extenso del post y cualquier info que nesecitan me la piden.

Muchas gracias
Slds

---

### Post by gmunioz on 2009-12-08
Hola ren....:

Ejecuta en consola:

```
sudo update-grub
```

---

### Post by RENGOdeDIA on 2009-12-08
Gracias gmunioz,
corri  sudo update-grub

me tiró esto

```

cesar@cesar-desktop:~$ sudo update-grub
[sudo] password for cesar: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

cesar@cesar-desktop:~$ 


```

pero cuando reinicio solo me muestra el 2.6.31-14
el grub es el 1.97 beta 4

Alguna otra sugerencia ?
Gracias

---

### Post by gmunioz on 2009-12-08
Hola ren....:

Por lo que se ve, tienes instalado el Grub2 en el mbr
y tienes el Grub legacy en el sistema.

Instala el Grub2 en el sistema, (grub2, grub-common. grub-pc)
desde synaptic, marca para desinstalar, si no se marcó automáticamente
el grub, aplica, sal de synaptic

Ejecuta 

sudo update-grub

Tendría que actualizarse el grub.cfg y no el menu.lst

---

### Post by RENGOdeDIA on 2009-12-08
Gracias de nuevo, esta vez lo pude resolver haciendo esto:

 > 
Por lo que se ve, tienes instalado el Grub2 en el mbr
y tienes el Grub legacy en el sistema.

Instala el Grub2 en el sistema, (grub2, grub-common. grub-pc)
desde synaptic, marca para desinstalar, si no se marcó automáticamente
el grub, aplica, sal de synaptic

Ejecuta

sudo update-grub

Tendría que actualizarse el grub.cfg y no el menu.lst 


Efectivamente cuando marcas Grub2 se marca para instalar grub-pc (grub-common ya estaba instalado); y para desinstalar grub.

Y efectivamente se actualiza grub.cfg


```
cesar@cesar-desktop:~$ sudo update-grub
[sudo] password for cesar: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
cesar@cesar-desktop:~$
```

Lo marco como solucionado
Saludos!!!!

---

