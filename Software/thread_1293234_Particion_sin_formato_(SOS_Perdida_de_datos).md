---
title: "Particion sin formato (SOS Perdida de datos)"
date: 2009-10-16
forum: Software
---

### Post by gab0z on 2009-10-16
Hola foreros  Perdon por no presentarme, pero estoy en apuros realmente grandes. Les resumo mi historia. Un amigo me trajo un disco rígido de 40 GB el cual no le andaba. Mi maquina es un Sempron 3100 de 2.2 GHz, un HD Western Digital de 160 GB, y un MotherBoard nVIDIA Geforce 6100 SE con Audio, Lan y Video integrados.  El problema surgio cuando ,de corazon, intente arreglarle el disco en cuestion. El disco de mi amigo se encapricho y no booteo más de un día para el otro con el mensaje "No se encuentra el sistema operativo". Probe muchas cosas tanto desde mi particion de Win2 como desde mi particion de Ubuntu, asi como tambien con distros portables como Backtrack y Slax. Nada parecia funcionar, incluso con fdisk /dev/hda salia esto [http://paste.ubuntu.com/294338/](http://paste.ubuntu.com/294338/) -que por ahora no es lo que más me interesa-.  Hasta que por idiotez lei al pasar que el comando dd transfiere datos desde un disco a otro. Entonces manos a la obra -de la destruccion- y ejecute desde Ubuntu dd if=/dev/hda -> el disco de mi amigo of=/dev/sdb6 --> la particion NTFS con absolutamente TODA mi información, más mis trabajos prácticos, etc. Cuando me di cuenta del error habían pasado 5 segundos, y presione CONTROL + C.  Hice un ls en la partición, nada. Entre en Win2, "la unidad no tiene formato".  Para orientarlos un poco más aca esta un mapa de mis particiones:  1 - linux ext3 (Ubuntu) 2 - linux swap  3 - NTFS (WinXP) 4 - NTFS (Archivos en SOS)  ¿Es posible que los datos se hayan borrado en 5 segundos o solo se perdio el formato? ¿Como puedo recuperar los datos en caso de que se pueda?  Muchas gracias a todos de antemano!  Saludos!  GABO

---

### Post by guillermolisi on 2009-10-16
> **gab0z said:**
> Hola foreros  Perdon por no presentarme, pero estoy en apuros realmente grandes. Les resumo mi historia. Un amigo me trajo un disco rígido de 40 GB el cual no le andaba. Mi maquina es un Sempron 3100 de 2.2 GHz, un HD Western Digital de 160 GB, y un MotherBoard nVIDIA Geforce 6100 SE con Audio, Lan y Video integrados.  El problema surgio cuando ,de corazon, intente arreglarle el disco en cuestion. El disco de mi amigo se encapricho y no booteo más de un día para el otro con el mensaje "No se encuentra el sistema operativo". Probe muchas cosas tanto desde mi particion de Win2 como desde mi particion de Ubuntu, asi como tambien con distros portables como Backtrack y Slax. Nada parecia funcionar, incluso con fdisk /dev/hda salia esto [http://paste.ubuntu.com/294338/](http://paste.ubuntu.com/294338/) -que por ahora no es lo que más me interesa-.  Hasta que por idiotez lei al pasar que el comando dd transfiere datos desde un disco a otro. Entonces manos a la obra -de la destruccion- y ejecute desde Ubuntu dd if=/dev/hda -> el disco de mi amigo of=/dev/sdb6 --> la particion NTFS con absolutamente TODA mi información, más mis trabajos prácticos, etc. Cuando me di cuenta del error habían pasado 5 segundos, y presione CONTROL + C.  Hice un ls en la partición, nada. Entre en Win2, "la unidad no tiene formato".  Para orientarlos un poco más aca esta un mapa de mis particiones:  1 - linux ext3 (Ubuntu) 2 - linux swap  3 - NTFS (WinXP) 4 - NTFS (Archivos en SOS)  ¿Es posible que los datos se hayan borrado en 5 segundos o solo se perdio el formato? ¿Como puedo recuperar los datos en caso de que se pueda?  Muchas gracias a todos de antemano!  Saludos!  GABO
Para mi no tiene vuelta atras. Asi como usaste el comando dd lo que se estaba llevando a cabo era una copia fisica de un disco a una particion, con lo cual al interrumpirla la informacion alojada en el track 0 del disco se altero pero nunca se termino de completar, por eso los mensajes de que el disco no tiene formato.

Ojala me equivoque en mi apreciacion.

---

### Post by gmunioz on 2009-10-17
Utiliza desde un live -cd testdisk

---

### Post by guillermolisi on 2009-10-17
> **gmunioz said:**
> Utiliza desde un live -cd testdisk
Gabriel, pensas que podra recuperar contenido o el testdisk es para probar el disco que estaba en duda ?

---

### Post by gmunioz on 2009-10-17
Hola Guillermo:

Estimo que en 5 segundos, a lo sumo alcanzo a borrar los

primeros bits de /dev/sdb6, asi que la información esta 

seguramente intacta.

Con testdisk se recuperan particiones formateadas, asi

que me parece que puede recuperar su disco.

distinto hubiera sido si hubiera utilizado if=/dev/zero

aunque tambien se podría haber intentado aunque con menos

esperanzas de recuperación.

Edito:

Leyendo mas detenidamente, incluso puede utilizar testdisk

desde Ubuntu.

Microsoft dice:

```
Para recuperar un volumen NTFS eliminado

   1. Vuelva a crear el mismo volumen exacto pero no elija formatearlo. 
Esto puede ser difícil si no recuerda el tamaño exacto que había creado
 originalmente, especialmente porque el complemento Administración de 
discos tiende a redondear los tamaños de particiones.
   2. Con Dskprobe.exe, recupere el sector de inicio de copia de seguridad
 del volumen NTFS que hay al final del volumen. Como es un volumen dinámico, 
quizás tenga que utilizar Dmdiag.exe para encontrar el sector de inicio de 
copia de seguridad o puede buscarlo utilizando Dskprobe.exe (en el menú Tools, 
haga clic en Search Sectors).
   3. Después de volver a escribir el sector de inicio de NTFS, salga de 
Dskprobe.
   4. En Administración de discos, haga clic en Volver a examinar los 
discos en el menú Acción. Esto debería montar el volumen para su uso 
inmediato.
```
Si bien este es un foro Ubuntu, la emergencia merece la cita. 8)

---

### Post by gab0z on 2009-10-20
Hola amigos/as.  Increiblemente me paso lo menos esperado. En mi partición recupere 20 GB de 50 que tenia, mientras que en el disco de mi amigo pude recuperar todos sus datos. Hice los mismos procedimientos, solo que al disco de mi amigo le había hecho un dd if=/dev/zero y al mio un if=/dev/hda (el disco de mi amigo) of=/dev/sda bs=1024 count=1.  Con el photorec recupere algunas cosas, pero no así con el testdisk, de la misma forma que lo hice con el otro disco. En el pude entrar y ver la estructura completa después de un "deeper search".  Una terrible macana.  Bueno, de los errores se aprende.   Saludos y gracias por comentar!  GABO.

---

