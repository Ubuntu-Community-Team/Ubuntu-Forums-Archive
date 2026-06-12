---
title: "[SOLVED] Sigo con dudas con el Grub."
date: 2008-07-26
forum: Software
---

### Post by pol666 on 2008-07-26
Ando con unas dudas con el Grub cuando instalo varias distribuciones...

El tema es que ya estuve planeando mi nuevaz tabla de particiones, y reserve 5gb para instalar un Mandriva Spring ahora el tema es el siguiente.

Yo instalo Mandriva spring luego de poner el win2, Mandriva me deja su GRUB. Hasta ahi OK.
Luego instalo Ubuntu, este saca el grub de mandriva y me pone Su grub.  Hasta ahi Ok 

Que pasa si yo el dia de mañana saco Mandriva, y pongo por ejemplo: Fedora. [B]¿El grub pasa a ser el de Fedora o sigo conservando el grub de ubuntu?
[/B]
[B]
En sintesis, el grub que use, depende el orden de la particion en el disco? o del orden de que particion instale primero?[/B]


Otra cosa, si yo pongo en un particion aparte "/boot", me facilitaria el cambio de distribuciones o seria lo mismo?

---

### Post by Mauro22 on 2008-07-26
Cada distro actualizara.

Hay dos formas de instalar el grub: 

Al inicio del disco
Al MBR

Si lo instalas en el MBR vas a tener un solo grub con todas las opciones que encuentre.

Si lo instalas al inicio del disco, vas a tener tantos grubs, como discos :D

---

### Post by pol666 on 2008-07-26
con MBR te referis a /boot?


No entendi mucho que digamos... Lo que quiero hacer es que una Sola distribucion me administre el grub, si es posible que sea Ubuntu (por que estoy seguro que esa no la voy a remover.)

---

### Post by Mauro22 on 2008-07-27
El grub no depende de la distro, el grub es siempre el mismo solo que cada distro lo personaliza y lo escribe en /boot (de la ultima que instalaste)

---

### Post by pol666 on 2008-07-27
Muchas Gracias, no importa si no entendi eswtoy dispuesto a romper todo si hace falta jaja

---

### Post by Ptero-4 on 2008-07-27
Inicio de la partición (no del disco como dijo otro) y MBR no se refieren a ubicaciones en el sistema de archivos. El inicio de la partición es los primeros 512 bytes de la partición (no se muestran en el gestor de archivos) y el MBR son los primeros 512 bytes del disco duro (va antes de la primera partición del disco y tampoco sale en el gestor de archivos), también grub no tiene un orden de instalación especifico, cada distribución pone grub en el MBR por omisión así que el que queda es el de la última distro instalada (a menos que le indiques que ponga el grub en el inicio de la partición que contiene la carpeta /boot (la cual puede ir en / o como partición independiente) ya que en ese caso tu solo agregas la entrada adecuada al grub actualmente instalado en el MBR para que te incluya una entrada para tu nueva distro).

---

### Post by pol666 on 2008-07-27
Entonses que recomiendan hacer una particion para /boot o no?

---

### Post by crosssover on 2008-07-28
yo me hice una particion /boot y se me solucionaron varios problemas que tenia antes, tambien cone so pude hacer dual boot de ubuntu + xp con el win en un disco esclavo asi no me jode el grub cada vez que lo reinstalo

---

### Post by pol666 on 2008-07-28
solved, no hice ninguna paticion para /boot. Instale Windows, Mandriva y despues Ubuntu, mand el startup manager y me quedo joya.

---

