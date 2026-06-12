---
title: "Como montar y desmontar unidades?"
date: 2009-06-27
forum: Software
---

### Post by xc36e on 2009-06-27
Estoy a oscuras todavia con linux y no logro entender como funciona esto del montaje y desmontaje de unidades.
Alguien sabe como tendria que hacer para montar mi antiguo disco D:\ de mi windows _desde la terminal_?.
Se que esta la funcion **mount** pero no logre indicarle bien los parametros supongo..

Gracias!

---

### Post by Hei Ku on 2009-06-27
Lo pasé como un post aparte porque no tiene nada que ver con los scripts, mas alla de que ambos se ejecutan por terminal.

---

### Post by rubioo on 2009-06-27
Para montar sistemas de archivos se utiliza el comando **mount**

 ```
# mount [dispositivo] [punto_de_montaje]
```

 El parametro **[dispositivo]** indica el dispositivo, como podría ser **/dev/sda1**.
 Y el campo **[punto_de_montaje]** representa cuál será el directorio de acceso
 a ese dispositivo.
 
 Para poder acceder al contenido de otra partición tendrías que poner:

 **# mount /dev/sda1 /media/disk-1**

 Si montamos, tenemos que desmontar.
 Cuando terminas de utilizar la unidad, por ejemplo si es un cd, la tapa de la 
 lectora no se va a abrir hasta que no este desmontado el dispositivo.

 ```
# umount /media/disk-1
```

 
 Saludos :)

---

### Post by Mister X on 2009-06-27
si la particion que queres montar te aparece en el archivo /etc/fstab es muy facil, simplemente tenes que escribir 
```
mount <particion>
```
y todas las opciones de montaje las toma desde dicho archivo, en caso de que no esté, las tenes que escribir cada vez que lo montas (te conviene agregarlo al fstab y ahorras trabajo)

---

### Post by xc36e on 2009-06-28
g

---

### Post by xc36e on 2009-06-28
Gracias por sus respuestas

quote=Hei Ku;7526137]Lo pasé como un post aparte porque no tiene nada que ver con los scripts, mas alla de que ambos se ejecutan por terminal.[/quote]

Ok gracias Hei Ku. y diculpá, fue por ignorancia. :) (para eso estamos)


> **rubioo said:**
> Para montar sistemas de archivos se utiliza el comando **mount**

 ```
# mount [dispositivo] [punto_de_montaje]
``` El parametro **[dispositivo]** indica el dispositivo, como podría ser **/dev/sda1**.
 Y el campo **[punto_de_montaje]** representa cuál será el directorio de acceso
 a ese dispositivo.
 
 Para poder acceder al contenido de otra partición tendrías que poner:

 **# mount /dev/sda1 /media/disk-1**

 Si montamos, tenemos que desmontar.
 Cuando terminas de utilizar la unidad, por ejemplo si es un cd, la tapa de la 
 lectora no se va a abrir hasta que no este desmontado el dispositivo.

 ```
# umount /media/disk-1
``` Saludos :)

Gracias rubioo por la ayuda.. y ahora necesito una explicacion porque me doy cuenta que me perdi mas.
bien, la sintaxis es: **mount** [dispositivo] [punto_de_montaje]
Como lo llamo a el dispositivo? Esta bien yo me fijo en **/dev/** y hay ficheros llamados **sdaX**.
Entre alguno de estos está el disco? o me estoy fijando en cualquier lado? digo.. :roll:  jeje

¿Como se cual es? 
¿El punto de montaje es indiferente? (tomamos como opcion /media)

Al instalar mi ubuntu anteriormente tenia el windows en disco C, y en el D tenia los datos de mis documentos y etc. ubuntu lo instale en el espacio libre del disco C. nose si esto seria de ayuda.

Haciendo un par de intentos, me pedia que especificara el tipo de sistema de archivos.
significa que tengo que escribir "ntfs"? gracias por la atencion

> **Mister X said:**
> si la particion que queres montar te aparece en el archivo /etc/fstab es muy facil, simplemente tenes que escribir 
```
mount <particion>
```y todas las opciones de montaje las toma desde dicho archivo, en caso de que no esté, las tenes que escribir cada vez que lo montas (te conviene agregarlo al fstab y ahorras trabajo)


Esta bien, a ese archivo habia llegado.. pero no comprendi nada en su interior.. 
¿Como lo tendria que modificar? sabiendo que ahora es asi:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=181848c3-8f2c-4016-bd97-60ebd8d50ec9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=bcacf5bc-05e0-47a4-b6f9-a1201dccba31 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Que funcion cumple este archivo? Estos son los que se inician al principio con la pc? porque seria lo que tambien estoy buscando.


gracias por la paciencia. :popcorn:

---

### Post by staar on 2009-06-28
el comando ```
sudo fdisk -l
``` te muestra como está particionado tu disco, con los nombres de las particiones, los tamaños y otras cosas, podés usarlo para darte un idea...

si la partición es la segunda con sistema de archivos identificable por windos (por eso ese sistema la llama D: en su notación), entonces en la salida del fdisk tenés que buscar la segunda partición con sistema de archivos de windos (supongo que será NTFS)

el punto de montaje puede ser cualquier carpeta, que hayas creado previamente...

el fstab es el archivo desde donde el sistema lee donde debe montar cada cosa en el inicio, en el tuyo no explicita ninguna partición de windos, para conocer más sobre este archivo (y sobre casi cualquier comando) podés correr ```
man fstab
``` sirve también para mount ```
man mount
```

generalmente no hace falta especificar el sistema de archivos, la autodetección funciona bien...

saludos

---

### Post by xc36e on 2009-06-28
> **staar said:**
> el comando ```
sudo fdisk -l
``` te muestra como está particionado tu disco, con los nombres de las particiones, los tamaños y otras cosas, podés usarlo para darte un idea...

si la partición es la segunda con sistema de archivos identificable por windos (por eso ese sistema la llama D: en su notación), entonces en la salida del fdisk tenés que buscar la segunda partición con sistema de archivos de windos (supongo que será NTFS)

el punto de montaje puede ser cualquier carpeta, que hayas creado previamente...

el fstab es el archivo desde donde el sistema lee donde debe montar cada cosa en el inicio, en el tuyo no explicita ninguna partición de windos, para conocer más sobre este archivo (y sobre casi cualquier comando) podés correr ```
man fstab
``` sirve también para mount ```
man mount
```generalmente no hace falta especificar el sistema de archivos, la autodetección funciona bien...

saludos

Gracias a lo que me dijiste logre saber el nombre de la particion que preciso. Esta sería **/dev/sda5**.
Hice lo siguiente :

**$** **sudo mount /dev/sda5 /media/disk**
y me dio esto:
fuse: failed to access mountpoint /media/disk: No existe el fichero ó directorio

Sin embargo si hago

**$ sudo mount /dev/sda5 /media**
Se logra montar el disco pero claro, tomando como raiz la carpeta media.

alguna idea che ? :confused: (ya casi estamos) jeje:)

---

### Post by staar on 2009-06-28
la carpeta donde querés montar la partición debe existir antes de montarla, para crear un directorio desde la terminal, se usa el comando mkdir, siguiendo tu ejemplo, antes tendrías que hacer ```
sudo mkdir /media/disk
```

en realidad, la carpeta /media, es donde el sistema (en realidad, lo hace HAL), monta automáticamente cosas como cds, dvds, particiones de windos, etc., para el montaje manual, históricamente se usó la carpeta /mnt, pero en realidad podés usar cualquier carpeta a la que tengas acceso...

otra cosa, si no lo sabés, el comando para desmontar es ```
umount /dev/sda5
```

saludos

---

### Post by xc36e on 2009-06-28
Solucionado.
Muchas Gracias por la colabolación. :popcorn:

---

