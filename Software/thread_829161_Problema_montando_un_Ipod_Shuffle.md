---
title: "Problema montando un Ipod Shuffle"
date: 2008-06-14
forum: Software
---

### Post by sdm_cacto on 2008-06-14
Buenas, me mande una c@g@d@ estando mi Ipod Shuffle montado, entre a sus propiedades y cambie el punto de montaje, a partir de eso cuando lo conecto no se monta automaticamente por algun error en lo q cambie.

Lo q necesito es montarlo manualmente pero no tengo ni idea de donde esta (/dev/sda1? sda2?) no entiendo mucho el tema del mount.

el error q me tira cuando lo intenta montar automaticamente es:
"No se puede montar el volumen
mount_point cannot contain the following characters: newline , G_DIR_SEPARATOR (usually /)

muchas gracias muchachos/as.

---

### Post by sdm_cacto on 2008-06-19
Alguien me ayuda?? esto es lo importante.

> Lo q necesito es montarlo manualmente pero no tengo ni idea de donde esta (/dev/sda1? sda2?) no entiendo mucho el tema del mount.

---

### Post by juanman on 2008-06-19
Hay muchas formas de saber cual es el dispositivo de tu ipod. Una es, despues de conectarlo, escribir en consola
```
sudo fdisk -l
```
Te va a listar todos los discos conectados a la pc con sus particiones (no importa q no estén montadas). Tu ipod probablemente sea /dev/sdb y suelen tener 2 particiones, asi q tal vez te aparezca /dev/sdb2 y /dev/sdb1...
Entonces para montarlo manualmente escribis:
```
sudo mount /dev/sdb2 /media/ipod -t vfat
```
donde: /dev/sdb2 es el dispositivo que te apareció antes;
/media/ipod es el punto de montaje, tiene q ser una carpeta q ya exista
-t vfat se le indica el sistema de archivos que usa la particion (en el caso de los ipods es fat32, y el kernel de linux lo identifica como vfat)

Igualmente creo q deberías entrar a las propiedades y cambiar el punto de montaje, a por ej, /media/ipod o /media/sdb2...

Saludos
Preguntá cualquier cosa

---

### Post by sdm_cacto on 2008-06-23
Gracias, tu respuesta era justo lo q buscaba.

---

