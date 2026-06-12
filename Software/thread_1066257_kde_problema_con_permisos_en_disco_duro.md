---
title: "kde problema con permisos en disco duro"
date: 2009-02-10
forum: Software
---

### Post by tsueseres on 2009-02-10
kde montaje de disco duro automatico
hola tengo gnome y kde en gnome cambie el fstab para que me montara automaticamente un disco duro, todo salio bien puedo copiar y pegar archivos y no me marca problemas,

cuando inicio en kde el dico se carga automaticamente pero cuando intento copiar algun archivo al disco duro me sale error de que no se pudieron cambiar los permisos,

saben como solucionar esto?

este es mi fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=8d7d8bed-00b4-40b1-9b0d-a242397edcf4 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

#/dev/sda7
UUID=aa21b533-3173-4a34-8314-19d0d6046266 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0

#disco a montar automaticamente
/dev/sda1 /media/luis ntfs auto,rw,exec,users,dmask=000,fmask=111,nls=utf8 0 0

---

### Post by clasificado on 2009-02-10
¿Pero copia? Por ahi te tira error de que no puede cambiar los permisos, pero copia

clasificado

---

### Post by tsueseres on 2009-02-12
> **clasificado said:**
> ¿Pero copia? Por ahi te tira error de que no puede cambiar los permisos, pero copia

clasificado

si, si  copia pero como puedo arreglar esto

---

### Post by tsueseres on 2009-02-15
nadien sabe como?

---

### Post by Hei Ku on 2009-02-15
Que te dice sobre ese disco si vas por el administrador de discos?
Deberias tener permisos de escritura como usuario.

---

### Post by guillermolisi on 2009-02-17
> **tsueseres said:**
> kde montaje de disco duro automatico
hola tengo gnome y kde en gnome cambie el fstab para que me montara automaticamente un disco duro, todo salio bien puedo copiar y pegar archivos y no me marca problemas,

cuando inicio en kde el dico se carga automaticamente pero cuando intento copiar algun archivo al disco duro me sale error de que no se pudieron cambiar los permisos,

saben como solucionar esto?

este es mi fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=8d7d8bed-00b4-40b1-9b0d-a242397edcf4 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

#/dev/sda7
UUID=aa21b533-3173-4a34-8314-19d0d6046266 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0

#disco a montar automaticamente
/dev/sda1 /media/luis ntfs auto,rw,exec,users,dmask=000,fmask=111,nls=utf8 0 0
Por que configuras la mascara para directorios en 000 (dmask) y la de archivos en 111 (fmask) ?

Tengo entendido que esos parametros son exclusivos para montar filesystems FAT y vos estas indicando que es NTFS.

Deberian ir los siguientes parametros, si hacen falta y el filesystem es realmente NTFS:
```
**uid**=value, **gid**=value and **umask**=value
              Set the file permission on the filesystem.  The umask  value  is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.
```

---

### Post by tsueseres on 2009-02-18
> **Hei Ku said:**
> Que te dice sobre ese disco si vas por el administrador de discos?
Deberias tener permisos de escritura como usuario.

el disco es ntfs cuando lo dejo montado en gnome no me da problemas, pero en kde cuando lo dejo montado y trato de mover o copiar algo hay me sale de que no se pudieron cambiar los permisos

esta es la linea que uso para montarlo en el fstab
/dev/sda1 /media/Luis ntfs auto,rw,exec,users,dmask=000,fmask=111,nls=utf8 0 0

---

### Post by tsueseres on 2009-02-18
> **guillermolisi said:**
> Por que configuras la mascara para directorios en 000 (dmask) y la de archivos en 111 (fmask) ?

Tengo entendido que esos parametros son exclusivos para montar filesystems FAT y vos estas indicando que es NTFS.

Deberian ir los siguientes parametros, si hacen falta y el filesystem es realmente NTFS:
```
**uid**=value, **gid**=value and **umask**=value
              Set the file permission on the filesystem.  The umask  value  is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.
```

no se de esas cosas entonces no podrias explicarmelo mejor y decirme que poner

---

