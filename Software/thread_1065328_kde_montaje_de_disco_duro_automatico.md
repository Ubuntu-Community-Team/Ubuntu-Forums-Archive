---
title: "kde montaje de disco duro automatico"
date: 2009-02-09
forum: Software
---

### Post by tsueseres on 2009-02-09
hola tengo gnome y kde en gnome cambie el fstab para que me montara automaticamente un disco duro, todo salio bien puedo copiar y pegar archivos y no me marca problemas,

cuando inicio en kde el dico se carga automaticamente pero cuando intento copiar algun archivo al disco duro me sale error de que no se pudieron cambiar los permisos, 

saben como solucionar esto?

este es mi fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=8d7d8bed-00b4-40b1-9b0d-a242397edcf4 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

#/dev/sda7
UUID=aa21b533-3173-4a34-8314-19d0d6046266 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0

#disco a montar automaticamente
/dev/sda1 /media/luis ntfs auto,rw,exec,users,dmask=000,fmask=111,nls=utf8 0 0

---

