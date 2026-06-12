---
title: "No Puedo Borrar directorios ni como root"
date: 2008-08-24
forum: Software
---

### Post by N1C0142 on 2008-08-24
yo tengo el mismo problema no puedo borrar nada de nada de mi pc .

tengo un pc viejo que me sirve de servidor y  tiene edubuntu  y me conecto a el atraves de ssh hasta ahi todo bien. 
pero cuando entro a los discos duros de la vieja maquina por ssh  no me deja borrar las carpetas ni ningun otro archivo intente cambiar los permisos como root pero no los cambia ,los discos estas en Vfat 32  tiene algo que ver esto.

ademas de que cuando copio archivos los copio lentamente a 1 MB/s 
cuando las tarjetas son de 100 Mb/s

---

### Post by Hei Ku on 2008-08-24
Fijate cómo está montando las particiones. FAT32 no tiene permisos por sí mismo, fijate que no la estes montando como read-only o solo para root, etc.

---

### Post by sherwoodinc on 2008-08-24
Probá montarlo con las opciones "rw,umask=0" , eso en general te da permiso de escritura aunque no seas root.

---

