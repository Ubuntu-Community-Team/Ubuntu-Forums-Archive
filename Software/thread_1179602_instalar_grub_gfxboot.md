---
title: "instalar grub gfxboot"
date: 2009-06-05
forum: Software
---

### Post by obedlink on 2009-06-05
hola

ya me he tronado ubuntu 3 veces por querer instalar un grub grafico, el famoso gfxboot.

desinstalo el grub
```
sudo aptitude remove grub
```

instalo gfxboot
```
sudo dpkg -i grub-gfxboot_0.97-11_i386.deb
```

instalar el grub
```
sudo grub-install /dev/sda
```

en este ultimo paso es donde no se que hacer, hay que instalar el grub donde estaba originalmente instalado. al algunas web he visto que dicen que es la particion donde tengo instalado ubuntu. en mi caso seria /dev/sda6.

en otras dicen que en el archivo menu.list en la linea donde esta el kernel, pero en mi menu.list no aparece nada.

adjunto los archivos menu.list y el resultado del comando "fdisk -l" para que me digan donde instalar el grub.

de todos modos he intentado ejecutar ```
sudo grub-install /dev/sda6
``` y me da como resultado "el archivo /boot/grub/stage1 no fue leido correctamente"

quiero aclarar que tengo instalado windows vista en una partición. que seria en la /dev/sda1.

espero puedan ayudarme.

---

### Post by staar on 2009-06-05
es un parto instalar gfxboot, pero anda (yo lo tengo andando), GRUB se instala normalmente en /dev/sda SIN ningún numero, que corresponde a la MBR del disco, instalarlo en una partición (/dev/sda6) es más complicado y no recomendado, a menos que sepas lo que estas haciendo...

asi que tenés que correr ```
sudo grub-install /dev/sda
``` y después ```
sudo update-grub
```

saludos

---

### Post by labinnsw on 2009-06-05
Deleted comment

---

### Post by Hei Ku on 2009-06-05
This is a Spanish-speaking forum. No need to repost in English.

Este es un foro español, no hay necesidad y no se recomienda escribir en ingles.

---

### Post by obedlink on 2009-06-05
> **staar said:**
> es un parto instalar gfxboot, pero anda (yo lo tengo andando), GRUB se instala normalmente en /dev/sda SIN ningún numero, que corresponde a la MBR del disco, instalarlo en una partición (/dev/sda6) es más complicado y no recomendado, a menos que sepas lo que estas haciendo...

asi que tenés que correr ```
sudo grub-install /dev/sda
``` y después ```
sudo update-grub
```

saludos

otra aclaracion, inicialmente todo el disco estaba siendo usado por windows vista, luego instale ubuntu de forma automatica, es decir yo solo escogi el espacio a usar por ubuntu y el solo hizo el resto (redimensionar el disco, particiones, formatear etc), de ahi aparen las particiones que muestra el comando "fdisk -l"

no estoy seguro que en uno de los intentos me dio por probar
```
sudo grub-install /dev/sda
``` desde sda a sda1,2,3,4,5,6 y en algunas medaba un mensaje de "el archivo /boot/grub/stage1 no fue leido correctamente" y en otra algo parecido aque no se podia acceder a la particion.

pero voy a volver a intentar, de todos modos con USB tardo solo 5 minutos en volver a instalar ubuntu :D

---

### Post by obedlink on 2009-06-05
ayuda
consola respondia
```
obed@obed-laptop:~/Escritorio$ sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.
obed@obed-laptop:~/Escritorio$
```

el mismo mensaje para sda1, sda5, sda6. ayuda, al pareces el archivo está malo, si sirve de ayuda, ese archivo no lo puedo abrir con gedit.

estoy usando ubuntu 9.04 puede ser la version de ubuntu?
si es posible que me ayudaran mientras tenga la PC encencidad, si me toca que volver a instar ubuntu.

---

### Post by staar on 2009-06-05
a ver, NO pruebes comandos, y menos si involucran a grub, y muchisimo menos tienen sudo (ahora no importa, porque podés reinstalar fácil, pero que no se te haga costumbre, porque algún dia podés romper todo) instalar grub en todas las particiones como estás haciendo te va a generar un lio bárbaro (y puede que V*sta quede inaccesible, si no lo está ya)

aclarado esto, primero comprobá que el paquete grub-gfxboot esté instalado correctamente, reinstalalo si es necesario...

después, instalá GRUB a la manera clásica:
```
sudo grub
``` y entras al intérprete de comandos de GRUB
```
find /boot/grub/stage1
``` para buscar la partición donde está la stage1
```
root (hdx,y)
``` reemplazando (hdx,y) por la salida del comando anterior
```
setup (hdx)
``` reemplazando solo el número de disco (el primero), SIN explicitar la partición
```
quit
```

y un ```
sudo update-grub
```

saludos

---

### Post by obedlink on 2009-06-05
grub> find /boot/grub/stage1

Error 15: File not found

el archivo si existe pero no se porque no lo encuentra :(

---

### Post by staar on 2009-06-05
a ver, para comprobar tu situación, podés acceder a V*sta y ubuntu? o, mejor dicho, al iniciar, te aparece GRUB?

saludos

---

### Post by obedlink on 2009-06-06
weno porque ya es tarde y la laptop la necesitan usar, reintale otra vez ubuntu, y duran la instalacion en la parte donde instala el grub, vi claramente que ejecuta el comando "grub-install /dev/sda" 

cuando reinicie no me aparecio el grub si no que aparecio la pantalla que aparece al usar el comando "sudo grub", pero igualmente se seguia dando el mensaje de
grub> find /boot/grub/stage1

Error 15: File not found

y bueno, ya reinstalado puedo entrar sin problemas a windows vista y ubuntu.

---

### Post by oktubrer on 2009-06-06
> **obedlink said:**
> y bueno, ya reinstalado puedo entrar sin problemas a windows vista y ubuntu.

Cuando instalé Jaunty desde cero tuve el mismo problema (de hecho todavía no lo pude solucionar y sigo con el grub clásico) pero te quería comentar que no es necesario que reinstales para resolverlo.  Hay varios métodos para restaurar el grub ahorrándote la reinstalación, en el foro hay algunos threads al respecto.

---

### Post by xurxoham on 2009-07-21
a mi tambien me pasa eso, y lo he hecho bien fijo, porque solo tengo un disco duro sata y ya he mirado la tabla de particiones usando el fdisk -l... el disco es sda obviamente y tambien me muestra el error en el stage1... hay alguna forma de actualizar ese archivo o es algo de la versión del SO, ya que estoy utilizando también el 9.04

---

### Post by Vash21 on 2009-08-04
Tengo el mismo problema que vosotros; he probado varios métodos y me ha sido imposible instalar el gfxboot en lugar del grub en ubuntu 9.04

¿Podría tener que ver que el sistema de archivos de la partición raíz sea ext4?

Saludos

---

### Post by Syrrio on 2009-09-29
Saludos, Yo tambien me apunto al problema :s estoy batallando ahora mismo con esto, solo comentar q no creo q sea por el ext4 pues mi ubuntu es el 9.04 pero aun asi mantuve el formato ext3

Al principio pensaba que podia ser causado por la arquitectura ya q estoy en uno de 64 pero segui investigando y encontre la variante para la instalacion, al final llego al mismo punto donde no se encuentra el archivo stage1 u_u

Ojala puedan encontrar la solucion o el porque del problema, no quiero usar el live cd T_T (jejeje y de momento tampoco apagar la compu) XD

Bytes

---

### Post by faktorqm on 2009-09-30
A mi me anduvo siempre, pero cada vez que necesitaba actualizar el grub se pisaba y tenia que repetir el procedimiento como si nunca lo hubiera instalado. Me canse un dia y lo deje asi no mas.

---

