---
title: "[OT] Problema para copiar archivo al system32"
date: 2013-06-29
forum: Software
---

### Post by wegweiser on 2013-06-29
Hola tengo un problema me falta el archivo ntoskrn en el system32 de mi computadora que tiene windows Xp y estoy abriendo el ubuntu como prueba desde un dvd, quiero copiar ese archivo al system y me dice errores de entrada y salida, como puedo hacer para que no pase esto?? me dijeron que si entraba como root iba a poder, que era una una cuestion de no tener permiso para realizar cambios, si es asi, como se hace esto? 
Otra cosa que queria hacer si no es abrir la ventana del DOS de xp en el ubuntu se puede??

---

### Post by MeduZa on 2013-07-05
XP no tiene DOS

---

### Post by guillermolisi on 2013-07-06
Si la particion donde reside WinXP es NTFS y esta corrupta, antes de trabajarla desde un LiveCD corre un scandisk con Windows para que resuelva inconsistencias en ese file system.
Eso se puede hacer con una sesion Live de PartedMagic, por ejemplo, que incluye herramientas para trabajar distintos tipos de file systems (y creo que hasta tiene una version mini de WinXP).

Que seas root en Linux no significa que lo seas para el sistema de seguridad propio de NTFS.

Si la particion Windows es FAT, entonces claramente es una cuestion de particion/file system corrupto y hasta podria ser problemas propios del disco rigido.

---

