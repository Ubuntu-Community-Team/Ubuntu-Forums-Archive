---
title: "Como montar una carpeta compratida en mi home???"
date: 2009-09-25
forum: Software
---

### Post by matias_tati on 2009-09-25
Hola que tal hace poco hize un post en donde preguntaba como compartir una carpeta, gracias a todos lo consegui. Ahora me sale una duda: dicha carpeta es una carpeta de musica que yo abro desde otro ordenador que usa ubuntu tmbn pero solamente consegui cargar la biblioteca con el rhytmbox y no con otro programa al no tener una direccion especifica donde buscar la carpeta, los navegadores de archivos de otros programas como el banshee no me la detectan...Hay manera de montar esta carpeta compartida en el home de dicha maquina para poder cargar las bibliotecas con ella, osea para buscar un directorio especifico con estos programas por ejemplo en el home de dicha maquina???
Espero haber sido claro. Gracias!!!!

---

### Post by electronpositivo on 2009-09-25
Probaste con el comando mount?

mount x.x.x.x:/carpeta_remota /home/usuario/carpeta_local

---

### Post by matias_tati on 2009-09-25
mount: sólo el usuario root puede efectuar esta acción

Y otra cosa de lograrlo asi tendria que efectuar este comando en cada inicio????

---

### Post by Hei Ku on 2009-09-25
hacelo por fstab, para que lo cargue solito.

agrega el recurso compartido al fstab. fijate que esta en los tutoriales de nfs

---

### Post by matias_tati on 2009-09-25
> **Hei Ku said:**
> hacelo por fstab, para que lo cargue solito.

agrega el recurso compartido al fstab. fijate que esta en los tutoriales de nfs

Si pero esto no es solo para carpetas compartidas con NFS??? Yo las tengo compartida con Samba

---

### Post by matias_tati on 2009-09-25
Lo hize siguiendo el tutorial este pero no pasa nada
Dejo el link y el ftsab que edite a ver si alguien me da una mano

[http://www.naguissa.com/blog.php?verpost&comentario=601](http://www.naguissa.com/blog.php?verpost&comentario=601)

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=4de70aeb-664e-48e6-9cb0-3ae08098e85f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=09fc10f0-d479-46c7-8dc2-d591b66715e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.1.2/mi%20música        /home/marcos/Música        smbfs    defaults,noatime,user,guest    1 1

---

### Post by Hei Ku on 2009-09-25
Que pasa si en una terminal ponés:

sudo mount -a

---

### Post by matias_tati on 2009-09-25
> **Hei Ku said:**
> Que pasa si en una terminal ponés:

sudo mount -a

marcos@marcos-desktop:~$ sudo mount -a
[sudo] password for marcos: 
Warning: mapping 'guest' to 'guest,sec=none'
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
marcos@marcos-desktop:~$

---

### Post by electronpositivo on 2009-09-25
> **matias_tati said:**
> 
Y otra cosa de lograrlo asi tendria que efectuar este comando en cada inicio????
Para que se monte en cada inicio podrías probar lo siguiente:

1. Crea un nuevo fichero llamado montajes.sh y guardarlo en /etc/init.d/
#!/bin/sh
#en la línea siguiente escribe las órdenes que ejecutas cuando las tengas claras
mount origen destino 
exit 0

2. Agrégale permisos de ejecución al fichero:
sudo chmod +x /etc/init.d/unidades.sh

3. Crea enlaces simbólicos en los directorios de arranque:
sudo ln -s /etc/init.d/montajes.sh /etc/rc0.d/S98montajes.sh
sudo ln -s /etc/init.d/montajes.sh /etc/rc1.d/S98montajes.sh
sudo ln -s /etc/init.d/montajes.sh /etc/rc2.d/S98montajes.sh
sudo ln -s /etc/init.d/montajes.sh /etc/rc6.d/S98montajes.sh

---

### Post by matias_tati on 2009-09-26
> **electronpositivo said:**
> Para que se monte en cada inicio podrías probar lo siguiente:

1. Crea un nuevo fichero llamado montajes.sh y guardarlo en /etc/init.d/
#!/bin/sh
#en la línea siguiente escribe las órdenes que ejecutas cuando las tengas claras
mount origen destino 
exit 0

2. Agrégale permisos de ejecución al fichero:
sudo chmod +x /etc/init.d/unidades.sh

3. Crea enlaces simbólicos en los directorios de arranque:
sudo ln -s /etc/init.d/montajes.sh /etc/rc0.d/S98montajes.sh
sudo ln -s /etc/init.d/montajes.sh /etc/rc1.d/S98montajes.sh
sudo ln -s /etc/init.d/montajes.sh /etc/rc2.d/S98montajes.sh
sudo ln -s /etc/init.d/montajes.sh /etc/rc6.d/S98montajes.sh

Es que todavia no consegui montar el directorio.Espero respuesta.
Gracias!!!!!

---

### Post by matias_tati on 2009-09-26
Intente editar fstab nuevamente y me tiro esto:

[[img]http://h.imagehost.org/t/0057/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0057/Pantallazo)

---

### Post by gmunioz on 2009-09-26
Hola mat....:

Prueba hacer lo que te sugiere el sistema:

```
man mount.cifs
```

Investiga sobre:

Warning: **mapping 'guest**' to '**guest,sec=none'**

Estimo debes hacer algunas modificaciones

en el archivo de configuración de samba del

sistema que originalmente tiene los datos.

---

### Post by matias_tati on 2009-09-27
Ya esta lo logre siguiendo este tutorial de Samba priimero y abajo tiene l link para montar directorios compartidos. El problema era que necesitaba crear una carpeta en mi home donde montar la carpeta no lo podia hacer directamente en mi home... Gracias...

[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)

---

### Post by Hei Ku on 2009-09-27
Siempre que montas algo tenes que tener la carpeta donde montarlo ya creada. Y la carpeta tiene que estar vacía o te estás buscando problemas.

---

### Post by matias_tati on 2009-09-27
> **Hei Ku said:**
> Siempre que montas algo tenes que tener la carpeta donde montarlo ya creada. Y la carpeta tiene que estar vacía o te estás buscando problemas.

No lo sabia pero es bueno saberlo ahora mismo estoy cargando las bibliotecas de Rhytmbox Banshee Exaile y Amarok como es la pc de mis hermanos no saben cual van a usar todavia, pero es buenisimo esto.
Bueno espero que a traves de mi problema mas gente pueda resolver sus dudas tmbn. Saludos!!!! Gracias!!!!

---

### Post by guillermolisi on 2009-09-27
> **matias_tati said:**
> No lo sabia pero es bueno saberlo ahora mismo estoy cargando las bibliotecas de Rhytmbox Banshee Exaile y Amarok como es la pc de mis hermanos no saben cual van a usar todavia, pero es buenisimo esto.
Bueno espero que a traves de mi problema mas gente pueda resolver sus dudas tmbn. Saludos!!!! Gracias!!!!
En realidad si se puede montar una particion en un directorio con contenido (algo absolutamente no recomendable), peeeero el contenido original de este directorio sera reemplazado por el contenido de la particion montada.

---

### Post by matias_tati on 2009-09-27
> **guillermolisi said:**
> En realidad si se puede montar una particion en un directorio con contenido (algo absolutamente no recomendable), peeeero el contenido original de este directorio sera reemplazado por el contenido de la particion montada.

Menos mal que no me salio....Saludos!!!

---

### Post by guillermolisi on 2009-09-27
> **matias_tati said:**
> Menos mal que no me salio....Saludos!!!
Me olvide aclarar que el reemplazo es mientras esa particion este montada. En cuanto las desmontas aparece el contenido original del punto de montaje nuevamente.

---

