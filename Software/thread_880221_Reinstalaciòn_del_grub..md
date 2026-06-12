---
title: "Reinstalaciòn del grub."
date: 2008-08-04
forum: Software
---

### Post by wanchan on 2008-08-04
Hola gente, teniendo linux y windows instalados en distintas particiones.
sda1: Windows
sda2: para datos
sda3: Ubuntu
sda4: Swap

Lo que hice fuè instalar nuevamente windows, en la particiòn C. Sabìa que al hacerlo me sobre escribirìa el grub en el MBR. Seguì los pasos que me indicaron en un pàgina de ubuntu-es para recuperarlo pero al llegar al punto de hacer
 $ sudo grub-install /dev/sda3 (en la particiòn donde tengo instalado ubuntu) no se instala y me da un error (en inglès) algo como que el formato no es compatible, no se si se refiere al sistema de archivos o algo no estoy haciendo bien. 
 Ya montè el sistemas ext3 de la particiòn en un directario ubicado en /media/ubuntu hice luego $ sudo chroot /media/ubuntu
hata ahì todo bien, el drama es lo anterior.
 Epero que alguien me ayude:(
Salu2!!

---

### Post by Mauro22 on 2008-08-04
Te conviene, arrancar con un livecd.

Una vez ahi, abris una consola y pones:

```
sudo grub
```Te va a quedar algo asi

```
grub>
```Ahi pones esto:

```
find /boot/grub/stage1
```y te va devolver algo como esto:

```
(hdx,y)
```Ahora pones:

```
root (hdx,y) *O sea lo que te dio antes
```y por ultimo:

```
setup (hdx)
```
Listo!:guitar:

---

### Post by wanchan on 2008-08-04
> **Mauro22 said:**
> Te conviene, arrancar con un livecd.

Una vez ahi, abris una consola y pones:

```
sudo grub
```Te va a quedar algo asi

```
grub>
```Ahi pones esto:

```
find /boot/grub/stage1
```y te va devolver algo como esto:

```
(hdx,y)
```Ahora pones:

```
root (hdx,y) *O sea lo que te dio antes
```y por ultimo:

```
setup (hdx)
```
Listo!:guitar:

En (hdx,y) la ¨x¨ lo reemplazo por la particiòn 3? y la ¨y¨?

---

### Post by Mauro22 on 2008-08-04
Eso seria el resultado de esta comando:

find /boot/grub/stage1

X es el disco
Y la particion.


Ejemplos:

Particion 3 disco 0
(hd0,3)

Particion 1 disco 1
(hd1,1)

---

### Post by ramiro_md on 2008-08-04
Cuanto usuarios victimas de problemas de grub hay !...por que no se hace una recopilacion de todos los threads referidos a problemas de grub ??...un saludo =)

---

### Post by wanchan on 2008-08-05
Muchas gracias mauro, pude recuperar el grub, la verdad no se que hice mal con el otro metodo. Una pregunta el comando sudo grup me devolvio (hd0,2) es decir disco 0, particion 2, es ahi donde esta instalado linux? o donde esta alojado el Grub?
 Por que con el comando fdisk -l me deci que linux esta instalado en sda3 y el swap en sda6.
 Gracias y saludos!

---

### Post by Hei Ku on 2008-08-05
sda3 corresponde al primer disco ( 0 ) y la tercera partición ( 2 ).
O sea, 
sd ---> hd
a ---> 0
3 ---> 2

Es que la nomenclatura de discos, que en este momento no me acuerdo como se llama, empieza a contar desde 0. Y el sd indica que lo toma como SCSI, SATA o similar, aunque muchas veces un IDE aparece también como sd, no es para preocuparse.
Así que está bien lo que te dice.

---

