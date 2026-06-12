---
title: "Problema despues de actualizar el kernel con Kubuntu 9.10"
date: 2009-12-07
forum: Software
---

### Post by darkside2009 on 2009-12-07
Hola muchachos,necesito ayuda para poder iniciar kubuntu otra vez.

Como vi que habia muchas actualizaciones por instalar,las instale y al reiniciar no puedo entrar a kubuntu.Al entrar en el boot me dice:

[CENTER]GNU GRUB Version 1.97 Beta 4(arriba,de titulo)[/CENTER]

[Minimal BASH-like line editing is supported.For the first word,TAB lists possible comands completions.Anywhere else TAB lists possible device/file completions]

sh:grub>_

Ahi intente con algunos comandos pero nada,no puedo hacer que inicie.Tambien busque en google y encontre esto:

[http://groups.google.com/group/iitdlug/browse_thread/thread/19e3fab24d9ae4c7](http://groups.google.com/group/iitdlug/browse_thread/thread/19e3fab24d9ae4c7)

Saludos

---

### Post by gmunioz on 2009-12-08
Hola dar....:

Si es que has instalado Ubuntu mediante Wubi, lo que no
informas, es un error de los sistemas de archivos ntfs,
que se repetirá con cada actualización.

Mi sugerencia es que rescates tus datos, e instales en
particiones propias, al menos tres /, /home, swap.

Para acceder a los datos alojados en una instalación hecha
con Wubi:

Inicia con el live cd de Ubuntu.

Monta la partición de Windows, suponiendo fuera /dev/sda1,
ejecuta en consola, Aplicaciones - Accesorios - Terminal:

```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mkdir /media/vdisk
sudo mount -o loop /media/win/ubuntu/disks/root.disk /media/vdisk
```

Tendras tus datos disponibles en /media/vdisk

Para corregir errores del sistgema de archivos, ejecuta:

```
sudo fsck /media/win/ubuntu/disks/root.disk
```

---

### Post by darkside2009 on 2009-12-08
Entonces,significa que voy a tener que reinstalar todo?

---

### Post by gmunioz on 2009-12-08
Puedes pasar una instalación hecha con wubi a particiones
comunes.

El sitio de la aplicación es este:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

La guia es esta:

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Particularmente, yo rescataria mis archivos y haría una nueva
instalación.

---

### Post by darkside2009 on 2009-12-08
Gracias Gmunioz,ya lo solucionè,guardè los archivos y reinstalè sin Wubi.Despues de instalarlo,actualizè el kernel y todo bien,el grub sigue estando.

Saludos

---

