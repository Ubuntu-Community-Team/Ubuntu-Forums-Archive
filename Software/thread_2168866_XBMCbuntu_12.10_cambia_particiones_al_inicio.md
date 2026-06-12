---
title: "XBMCbuntu 12.10 cambia particiones al inicio"
date: 2013-08-19
forum: Software
---

### Post by isidoro2 on 2013-08-19
Buenas, tengo un problema con un ubuntu 12.10 (xbmcbuntu),la pc tiene 4 discos 1 IDE y 3 SATA en el IDE esta el sistema y los sata son solo para datos, el tema está en que cuando lo instalé el tomo los 3 sata primero (sda, sdb, sdc) y el ide como sdd.

Cuando arranca se montan asi:
/dev/sdd1 on / type ext4 (rw,errors=remount-ro)
/dev/sda1 on /home/usuario/disco1 type ext3 (rw)
/dev/sdb1 on /home/usuario/disco2 type ext3 (rw)
/dev/sdc1 on /home/usuario/disco3 type ext3 (rw)

cuando es asi no hay probelma pero de MUY SEGUIDO arranca con las particiones cambiadas y me monta el disco IDE como sda.. y me arma quilombo con las otras particiones...

alguna idea??? gracias.....

---

### Post by gmunioz on 2013-08-21
Abre una terminal
Ejecuta en ella
> sudo su
fdisk -l
cat /etc/fstab
blkid
Copia y pega las salidas en el post.

---

### Post by isidoro2 on 2013-08-23
asi queda cuando arranca correctamente. los sda, sdb y sdc los monto a mano al inicio... por eso no están en el fstab... (hice esto como ultima opción para ver si se solucionaba)

probé ponerlos en el fstab y nada...



1 - fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa6dd4606


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953525167   976761560   83  Linux


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x939aa79b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   83  Linux


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73657250


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  1953520064   976760001   83  Linux


Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d9d3


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   152111101    76054527   83  Linux
/dev/sdd2       152111102   156301311     2095105    5  Extended
/dev/sdd5       152111104   156301311     2095104   82  Linux swap / Solaris



2- cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=5c4f060d6ce4409b87554a35c95965bb / ext4 errors=remount-ro 0 1
UUID=9425f94d6ef74893b77f8142fb01d2da none swap sw 0 0


3- blkid

/dev/sda1: UUID="87e403e1-27dd-4737-81ec-a52ca737c374" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="31e49b95-fa4e-4f19-a0da-52b34532e171" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="5c4f060d-6ce4-409b-8755-4a35c95965bb" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdd1: UUID="7f3399d7-6778-45bb-a18c-efba532164bc" TYPE="ext4"
/dev/sdd5: UUID="9425f94d-6ef7-4893-b77f-8142fb01d2da" TYPE="swap"

---

### Post by gmunioz on 2013-08-23
Edita tu archivo /etc/fstab
> sudo su
nano /etc/fstab
Y agrega las líneas
> #/dev/sda1
UUID=87e403e1-27dd-4737-81ec-a52ca737c374   /home/tu-usuario/disco1   ext3   defaults,errors=remount-ro    0    2   
#/dev/sdb1
UUID=31e49b95-fa4e-4f19-a0da-52b34532e171   /home/tu-usuario/disco3    ext3   defaults,errors=remount-ro    0    2   
#/dev/sdd1 
UUID=7f3399d7-6778-45bb-a18c-efba532164bc   /home/tu-usuario/disco2    ext4   defaults,errors=remount-ro    0    2   

Control + O guarda, Control + X cierra.
Verifica que esten creados los directorios (carpetas) en tu /home/tu-usuario/  disco1, disco2 y disco3
Sino los creas con:
> sudo su
mkdir /home/tu-usuario/disco1
mkdir /home/tu-usuario/disco2
mkdir /home/tu-usuario/disco3
Debes darle permisos antes de montar las particiones, a los directorios
> sudo su
chmod -Rf 777 /home/tu-usuario/disco1
chmod -Rf 777 /home/tu-usuario/disco2
chmod -Rf 777 /home/tu-usuario/disco3
Una vez terminado, para montar sin reiniciar ejecutas:
> sudo su
mount -a
Con esto, en cada inicio, se montaran las particiones como esta establecido en /etc/fstab
Sería de buena práctica, que al editar el archivo /etc/fstab añadas a las líneas:
> # <file system> <mount point> <type> <options> <dump> <pass>
UUID=5c4f060d6ce4409b87554a35c95965bb / ext3 errors=remount-ro 0 1
UUID=9425f94d6ef74893b77f8142fb01d2da none swap sw 0 0
Estas líneas aclaratorias
> 
# <file system> <mount point> <type> <options> <dump> <pass>
#/dev/sdc1
UUID=5c4f060d6ce4409b87554a35c95965bb / ext3 errors=remount-ro 0 1
#/dev/sdd5
UUID=9425f94d6ef74893b77f8142fb01d2da none swap sw 0 0

---

