---
title: "backup de sistema"
date: 2009-05-18
forum: Software
---

### Post by dirty fingers on 2009-05-18
Hola gente. ya puse mi ubuntu bonito y funcional (que la sude uffff) y ahora me gustaría hacer una copia de seguridad.

Lo único que encontré para hacerlo es "clonezilla-live-1.2.1-53"

El problema es que para particiones de ext4 entra en un modo de lectura bit a bit y te lee hasta el espacio vacío.

Tengo dos particiones con ext4; una con / y la otra con /home

No puse ningún archivo personal en /home para poder incluirlo en el backup ya que hay miles de configuraciones ahí guardadas.

*******. Cualquier sugerencia sirve. Gracias.

---

### Post by guillermolisi on 2009-05-18
> **dirty fingers said:**
> Hola gente. ya puse mi ubuntu bonito y funcional (que la sude uffff) y ahora me gustaría hacer una copia de seguridad.

Lo único que encontré para hacerlo es "clonezilla-live-1.2.1-53"

El problema es que para particiones de ext4 entra en un modo de lectura bit a bit y te lee hasta el espacio vacío.

Tengo dos particiones con ext4; una con / y la otra con /home

No puse ningún archivo personal en /home para poder incluirlo en el backup ya que hay miles de configuraciones ahí guardadas.

Estoy en bolas. Cualquier sugerencia sirve. Gracias.
CloneZilla clona discos, por eso hace copia fisica de cada sector del disco y no de lo que realmente se usa.

Hay gran cantidad de utilitarios. Algunos los podes encontrar en [GetDeb]("http://www.getdeb.net/browse.php"). Otros alternativos a los que ahi pueden figurar:

**rdiff** [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)
**Time Vault** [http://www.techthrob.com/2009/03/02/backing-up-in-ubuntu-made-easy-with-timevault-an-in-depth-review/](http://www.techthrob.com/2009/03/02/backing-up-in-ubuntu-made-easy-with-timevault-an-in-depth-review/) (review del producto)
**Rsync** [http://www.samba.org/rsync/features.html](http://www.samba.org/rsync/features.html)
Grsync [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/) (interface para Rsync)
**Sbackup** [http://sbackup.wiki.sourceforge.net/](http://sbackup.wiki.sourceforge.net/)

Y despues tenes cosas algo mas complejas que generalmente se usan para mas de una maquina en red o entornos corporativos (empresas) como es el caso de Bacula, Amanda y similares.

No te olvides, Google es tu amigo :) sobre todo cuando estas desnudo (de ideas).

---

### Post by dirty fingers on 2009-05-18
jaja no no , ya hice la tarea. recurri al foro luego de una hora de google. varios de esos que mensionas los vi, pero resultan útiles si todavía algo funciona. por ejemplo sbackup si se me palma el disco rigido o se borra completo voy a tener que instalar ubuntu, luego el programa y luego tirar el backup.
Buscaba algo mas contundente; onda el norton ghost para windows.

---

### Post by guillermolisi on 2009-05-18
> **dirty fingers said:**
> jaja no no , ya hice la tarea. recurri al foro luego de una hora de google. varios de esos que mensionas los vi, pero resultan útiles si todavía algo funciona. por ejemplo sbackup si se me palma el disco rigido o se borra completo voy a tener que instalar ubuntu, luego el programa y luego tirar el backup.
Buscaba algo mas contundente; onda el norton ghost para windows.
En ese caso CloneZilla o similar seria de aplicacion.

CloneZilla lo usamos en el laburo para poner en produccion cerca de 14 servidores en el 2007.
Hicimos uno y el resto salio como chorizos :), lo que dura la copia al disco rigido de la imagen obtenida. Encendimos cada maquina y "voilá", salieron funcionando.

---

### Post by EnriqueK on 2009-05-18
Probá en usar una versión del CloneZilla basada en Ubuntu Jaunthy , aunque es todavía de caracter experimental, creo que funciona correctamente.
[http://sourceforge.net/project/showfiles.php?group_id=115473&package_id=233347](http://sourceforge.net/project/showfiles.php?group_id=115473&package_id=233347)

---

### Post by Hei Ku on 2009-05-18
dd es lo mejor para backup en caso de desastre.

---

### Post by guillermolisi on 2009-05-18
Si, de hecho CloneZilla esta armado en torno a dd.

---

### Post by dirty fingers on 2009-05-23
Probé el Clonezilla basado en Ubuntu Jaunthy. Reconoció el ext4 sin problema así que la imagen solo ocupaba el espacio usado (menos lo ganado por la compresión).
Ahora la probe en Virtual Box y me dice que esta dañada.
Parece que le faltan algunos agustes mas para que funcione.

---

### Post by guillermolisi on 2009-05-23
> **dirty fingers said:**
> Probé el Clonezilla basado en Ubuntu Jaunthy. Reconoció el ext4 sin problema así que la imagen solo ocupaba el espacio usado (menos lo ganado por la compresión).
Ahora la probe en Virtual Box y me dice que esta dañada.
Parece que le faltan algunos agustes mas para que funcione.
Que significa "lo probe en Virtual Box" ?

Si queres hacer copia de una maquina virtual con copiar un par de archivos (el o los discos y el archivo de definicion en XML, alcanza para un backup).

---

### Post by dirty fingers on 2009-05-23
> **guillermolisi said:**
> Que significa "lo probe en Virtual Box" ?

Si queres hacer copia de una maquina virtual con copiar un par de archivos (el o los discos y el archivo de definicion en XML, alcanza para un backup).


que una vez que cree la imagen de mi partición simule restaurarla en una maquina virtual para confirmar que este bien.

---

### Post by guillermolisi on 2009-05-23
> **dirty fingers said:**
> que una vez que cree la imagen de mi partición simule restaurarla en una maquina virtual para confirmar que este bien.
Mmmm ... Las caracteristicas del disco generado en la VM deberian ser similares al original. Por lo menos su capacidad que no deberia ser menor asi puede restituir las particiones tal como las copio.

---

### Post by EnriqueK on 2009-05-23
Lo que te puedo decir es que la instalación de Jaunty la hice en EXT3 , luego después de instalar todos los programas le hice la conversión a EXT4 , pero antes creé una imagen de respaldo de mi instalación original en EXT3 , finalizado el proceso de conversión del sistema de archivos, creé otra imagen de respaldo usamdo el CloneZilla - Jaunty y que luego la usé para restaurarla, o sea hice la prueba cúlmine y definitiva, el resultado era el esperado, sin problemas.

---

### Post by dirty fingers on 2009-05-23
bueno. voy a probar de nuevo a ver que pasa. gracias a ambos.

---

