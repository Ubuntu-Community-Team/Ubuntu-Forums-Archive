---
title: "Como cambiar los nombres de los dispositivos montados"
date: 2009-08-21
forum: Software
---

### Post by Fistandantilus on 2009-08-21
Hola a todos!

Ayer por la noche me monte un servidor nfs para compartir archivos con la compu de mi viejo(otro ubuntu 9.04 en red local). Probe de montar los directorios y sin problemas, es mas me sorprendio la taza de tranferencia contra el samba).
Recien le configure el fstab para que no tenga que montarlos a manopla cada vez que quiera ver una peli de mi hdd pero quiero cambiarle el nombre para que no se equivoque, ya que exporte directamente el dir /media/sda5 y el ya tiene un /media/sda5 asi que se lo monte en /media/gera/sda5.
Una vez montado a el le aparece en el escritorio y en "lugares" "sda5", pero quiero ponerle algo asi como "sda5 en gera" para diferenciarlos...

estuve buscando en el gconf-editor y no encontre nada, tambien en todos los archivos que contengan el texto "Soporte" ya que tiene dispositivos montados con ese nombre dentro de gnome a ver si encontraba el archivo de conf y nada...

alguna idea???

Saludos!!

---

### Post by Hei Ku on 2009-08-21
Por que no le cambias el nombre al punto de montaje y listo? No tiene por qué llamarse igual.

---

### Post by rubioo on 2009-08-21
A mi me pasa algo parecido,  la partición que tiene Windows (que esta en el punto de montaje disk-1) esta con el nombre Soporte de 100,1 GiB. Y estaría bueno cambiarle el nombre.

---

### Post by Fistandantilus on 2009-08-21
Esa es una opción, pero tambien queria = que rubioo sacar los "Soporte de ..." etc... y mato 2 pajaros de un tiro

---

### Post by Hei Ku on 2009-08-21
> **rubioo said:**
> A mi me pasa algo parecido,  la partición que tiene Windows (que esta en el punto de montaje disk-1) esta con el nombre Soporte de 100,1 GiB. Y estaría bueno cambiarle el nombre.

No, tu problema es distinto, porque esto se trata de NFS. Abri un thread aparte.

---

### Post by rubioo on 2009-08-21
No hay problema Hei Ku.

---

### Post by Fistandantilus on 2009-08-21
> **Hei Ku said:**
> No, tu problema es distinto, porque esto se trata de NFS. Abri un thread aparte.

Creo q es el mismo problema, ya que por mas que los directorios esten montados desde un servidor nfs, esta montado como cualquier otro volúmen desde el fstab. Ademas ése nombre es algo particual de gnome, hasta me atrevería a decir q es algo particular del usuario, xq si inicio un nautilus como root, los mismos volúmenes que me aparecen nombrados como "Soporte de XXGb" en el usuario creado desde la instalación me aparecen como "sda1", "sda5" que son los nombres de las carpetas en el nautilus desde root.

---

### Post by Hei Ku on 2009-08-21
pone tu fstab

---

### Post by Fistandantilus on 2009-08-21
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda6 during installation
UUID=8ae56917-9700-424b-a130-e70325a8e4ed  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda1 during installation
UUID=f4fa9854-befa-4e6d-829b-87eaf5b74ab4  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda5                                  /media/sda5  ntfs         defaults                    0  0  
gera-desktop.local:/media/sda5    /media/gera/sda5    nfs    defaults    0    0
gera-desktop.local:/media/cdrom    /media/gera/cdrom    nfs    defaults    0    0

```

---

### Post by Hei Ku on 2009-08-21
vos lo montas en /media/gera/sda5

cambiando ese nombre a sda5_otra_pc o lo que sea, ya esta

---

### Post by EnriqueK on 2009-08-21
En relidad lo que querés es cambiar la etiqueta (label) del dispositivo montado, para particiones EXT 2 . EXT3 y EXT4  , tenés la función **e2label **
[http://manpages.ubuntu.com/manpages/dapper/man8/e2label.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/e2label.8.html)

Resumiendo, la sintáxis sería
**sudo e2label device [ new-label ]**


Por ejemplo en mi caso mi device está en /dev/sda6  y le quiero cambiar la etiqueta a E, entonces el comado será

sudo e2label /dev/sda6 E

Lo que resta es reiniciar el equipo .
Si las particiones las tenés en otro sistema de archivos, este método no sirve ya que es solo para EXT 2 . EXT3 y EXT4

---

### Post by Hei Ku on 2009-08-21
Alguien se paro a leer que es un share de nfs y no una particion?

---

