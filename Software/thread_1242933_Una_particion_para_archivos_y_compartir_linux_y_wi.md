---
title: "Una particion para archivos y compartir linux y windows"
date: 2009-08-17
forum: Software
---

### Post by feder1991 on 2009-08-17
Hola, tengo un disco partido en 2, ubuntu 9.04 y windows xp (por necesidad de algunos programas). El problema es que desde windows no puedo ver los archivos en linux y por eso me gustaria saber si puedo hacer una particion (no se en que formato sera mejor) para que pueda volcar los archivos ahi y editarlos desde los 2 sistemas operativos.

el problema que tengo tambien cuando entro desde ubuntu al disco de windows es que no esta montado, cosa que me j**e cada vez que prendo la pc montarlo. se puede hacer que este montado siempre??

gracias!! sigan asi!

---

### Post by feder1991 on 2009-08-17
alguien?

---

### Post by staar on 2009-08-17
si podés, el único problema es que vas a tener que usar NTFS, porque Ventanas no lee nativamente los sistemas de archivos de linux, podés hacerlo desde el livecd con el Editor de particiones (gparted), solo asegurate de que, si vas a achicar una partición de Ventanas (para hacer lugar para la nueva) esta debe estar bien desfragmentada, porque sino, o va a fallar, o va a tardar una eternidad...

para que te monte las particiones NTFS al inicio tenés que modificar el /etc/fstab existen programas gráficos para hacerlo, como disk manager o  ntfs-config, están en los repos...

saludos

---

### Post by oktubrer on 2009-08-17
En los repositorios está ntfs-config, una herramienta gráfica que te permite configurar las particiones ntfs fácilmente, permitiendo que se monten al inicio y además con permisos de escritura.
Con respecto al otro tema, existe una aplicación para windows [1] que te permite acceder a las particiones ext2 y ext3.  No se si soportará ext4 ya.

[1] [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Tosh78 on 2009-08-17
A mi los programas de windows nunca me funcionaron, nunca pude hacer que lean ext3, asi que supongo que menos van a leer ext4.
Si queres ir a lo seguro, hace como te decian, una particion de NTFS.

---

### Post by Fistandantilus on 2009-08-18
para configurar las particiones y que se monten automaticamente al inicio uso el pysdm.
lo encontras en synaptic y tenes acceso a el desde administracion en el menu.
[FONT=courier new]**[/FONT]

---

### Post by alejandromafer on 2009-08-19
Tenés que crear una particion ntfs. Yo uso ntfs-config para que la particion se monte al inicio del sistema

---

