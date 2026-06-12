---
title: "Problema con grub"
date: 2010-05-28
forum: Software
---

### Post by uburox on 2010-05-28
Hola que tal?

bueno paso a explicar cuál es el problema.

tengo un disco duro portaitl samsung S2 de 500Gb (USB)

el cual particione para instalar ubuntu 9.10 y el resto dejarlo para disco de datos (y backups)

hice la particion de ubuntu(195Gb) donde monte "/" y la de swap que la hice de 1Gb...................

todo bonito...
hasta que termino la instalacion y me dice error de grub


[COLOR="Red"][B]error:unknown filesystem
[/B][/COLOR]

ya baje el super grub disk....pero no logre que me funcione el grub..... me dice que SGD no lo logró =S



que es lo que puedo hacer?

a y en el cd de instalacion de ubuntu 9.10 cuando hago


sudo grub

para reinstalarlo me dice que no es un comando o algo asi....


buen oespero puedan ayudarme a la brebedad l
desde ya muchas gracias


[FONT="Comic Sans MS"][COLOR="Lime"][COLOR="lime"][COLOR="Black"]Uburox[/COLOR][/COLOR][/COLOR][/FONT]

---

### Post by uburox on 2010-05-29
[SIZE=5][COLOR=olive][B][SIZE=3]el problema estaba en que la particion de ubuntu no estaba al principio del disco [/SIZE]

[SIZE=3]y olvide montar el gestor en esa particion[/SIZE][/B][/COLOR][/SIZE]



> **uburox said:**
> hola que tal?

Bueno paso a explicar cuál es el problema.

Tengo un disco duro portaitl samsung s2 de 500gb (usb)

el cual particione para instalar ubuntu 9.10 y el resto dejarlo para disco de datos (y backups)

hice la particion de ubuntu(195gb) donde monte "/" y la de swap que la hice de 1gb...................

Todo bonito...
Hasta que termino la instalacion y me dice error de grub


[COLOR=red][B]error:unknown filesystem
[/B][/COLOR]

ya baje el super grub disk....pero no logre que me funcione el grub..... Me dice que sgd no lo logró =s



que es lo que puedo hacer?

A y en el cd de instalacion de ubuntu 9.10 cuando hago


sudo grub

para reinstalarlo me dice que no es un comando o algo asi....


Buen oespero puedan ayudarme a la brebedad l
desde ya muchas gracias


[FONT=comic sans ms][COLOR=lime][COLOR=lime][COLOR=black]uburox[/COLOR][/COLOR][/COLOR][/FONT]

---

