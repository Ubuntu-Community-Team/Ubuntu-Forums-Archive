---
title: "NTFS como home"
date: 2009-02-17
forum: Software
---

### Post by h9005 on 2009-02-17
Se puede usar una particion NTFS compartida como particion home de linux?

---

### Post by blackknightr89 on 2009-02-17
Entiendo que no. Sólo ext2 y ext3.

---

### Post by sherwoodinc on 2009-02-17
Si te sirve, podés montar particiones ext2 y ext3 desde xp (no sé si Vista) tanto para lectura como escritura con un driver que se instala (freeware):

[http://www.fs-driver.org/](http://www.fs-driver.org/)

A mí me simplificó las cosas más de una vez.

---

### Post by fmsismo on 2009-02-18
> **h9005 said:**
> Se puede usar una particion NTFS compartida como particion home de linux?

No podes usar ntfs como home, porque no podes administrar los permisos.

Podes montar las particiones ext2/ext3 en windows.  Pero tenes que tener cuidado porque al ext3 lo montas como ext2 (sin journal) y no es desmontada correctamente podes tener corrupción de datos.

Si lo que necesitas es aceder a tus documentos de windows en el linux, lo que yo haría sería.
[LIST=1]
[*]modificar el fstab para que monte la unidad ntfs en forma automática
[*]hacer un link simbólico entre en mi home que se llame WinDocs del directorio mis documentos de windows
[/LIST]

Saludos

---

