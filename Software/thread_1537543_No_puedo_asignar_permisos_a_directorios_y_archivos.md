---
title: "No puedo asignar permisos a directorios y archivos"
date: 2010-07-23
forum: Software
---

### Post by leonardomdq on 2010-07-23
Hola a todos, tengo un problema con los permisos en mi ubuntu.
El tema esa asi, tengo mi directorio de Música y dentro de el sub directorios a los cuales no puedo visualizar ni con MPD, Rhythmbox o el que use.
Si me logueo como root tampoco me permite modificarlos, propietarios y acceso a la carpeta si me deja, pero acceso al archivo no puedo.
Dejo una captura....alguna idea?

---

### Post by guillermolisi on 2010-07-23
Y si pasas la salida de ```
ls -al
```ingresado en consola/terminal ?

A mi me resulta mas comodo ver el tema asi y cambiar permisos desde la consola es mucho mas franco que a traves de la interface grafica.

---

### Post by leonardomdq on 2010-07-24
Hola guillermo, gracias por contestar.

**ls -al**
```

leonardo@ubuntu-desktop:~$ ls -al
total 1280
drwxr-xr-x 55 leonardo leonardo   4096 2010-07-24 11:05 .
drwxr-xr-x  4 root     root       4096 2010-07-04 20:05 ..
drwx------  3 leonardo leonardo   4096 2010-07-05 00:03 .adobe
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-23 23:00 Aplicaciones
-rw-------  1 leonardo leonardo  10679 2010-07-23 23:43 .bash_history
-rw-r--r--  1 leonardo leonardo    220 2010-07-04 20:05 .bash_logout
-rw-r--r--  1 leonardo leonardo   3103 2010-07-04 20:05 .bashrc
drwx------ 15 leonardo leonardo   4096 2010-07-24 11:05 .cache
drwx------  3 leonardo leonardo   4096 2010-07-04 21:29 .compiz
drwxr-xr-x 26 leonardo leonardo   4096 2010-07-23 09:47 .config
drwx------  2 leonardo leonardo   4096 2010-07-20 14:33 .conky
-rwxr-xr-x  1 leonardo leonardo   1736 2010-07-20 14:36 .conkyrc
-rw-r--r--  1 leonardo leonardo    817 2010-07-16 14:32 .conkyrc_clock
-rwxr-xr-x  1 leonardo leonardo   2657 2010-07-16 17:49 .conkyrc_rings
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-20 14:33 .covers
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-05 01:05 .cover-thumbnailer
drwx------  3 leonardo leonardo   4096 2010-07-04 20:18 .dbus
drwxr-xr-x  2 leonardo leonardo  12288 2010-07-24 11:17 Descargas
-rw-r--r--  1 leonardo leonardo     55 2010-07-24 11:05 .dmrc
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-21 14:14 .dockbarx
drwxr-xr-x 18 leonardo leonardo   4096 2010-07-23 22:58 Documentos
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-23 22:56 Dropbox
drwxr-xr-x  4 leonardo leonardo   4096 2010-07-20 20:24 .emerald
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-24 11:38 Escritorio
-rw-------  1 leonardo leonardo     16 2010-07-04 20:18 .esd_auth
drwxr-xr-x  7 leonardo leonardo   4096 2010-07-07 17:58 .evolution
-rw-r--r--  1 leonardo leonardo   2366 2010-07-13 15:30 .fehrc
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-22 14:43 .fontconfig
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-16 12:37 .fonts
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-23 23:01 Fotos
drwx------  5 leonardo leonardo   4096 2010-07-24 11:05 .gconf
drwx------  2 leonardo leonardo   4096 2010-07-24 11:16 .gconfd
drwx------  4 leonardo leonardo   4096 2010-07-05 14:51 .gegl-0.0
drwxr-xr-x 22 leonardo leonardo   4096 2010-07-23 23:10 .gimp-2.6
-rw-r-----  1 leonardo leonardo      0 2010-07-23 19:15 .gksu.lock
drwxr-xr-x 10 leonardo leonardo   4096 2010-07-23 00:04 .gnome2
drwx------  2 leonardo leonardo   4096 2010-07-04 20:19 .gnome2_private
drwx------  2 leonardo leonardo   4096 2010-07-20 19:07 .gnupg
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-20 12:14 .gstreamer-0.10
-rw-r--r--  1 leonardo leonardo    169 2010-07-24 11:05 .gtk-bookmarks
dr-x------  2 leonardo leonardo      0 2010-07-24 11:05 .gvfs
-rw-------  1 leonardo leonardo  21708 2010-07-24 11:05 .ICEauthority
drwxr-xr-x  7 leonardo leonardo   4096 2010-07-22 18:45 .icons
drwxr-xr-x 20 leonardo leonardo   4096 2010-07-22 21:00 Imágenes
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-23 23:02 Internet
drwxr-xr-x 12 leonardo leonardo   4096 2010-07-19 23:59 .jdownloader
drwx------  3 leonardo leonardo   4096 2010-07-04 21:14 .local
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-17 12:45 .lyrics
drwx------  3 leonardo leonardo   4096 2010-07-05 00:03 .macromedia
drwxr-xr-x  6 leonardo leonardo   4096 2010-07-05 00:02 .magicons
drwx------  3 leonardo leonardo   4096 2010-07-08 14:13 .mission-control
drwx------  4 leonardo leonardo   4096 2010-07-04 21:31 .mozilla
drwxr-xr-x  3 leonardo leonardo   4096 2010-07-24 11:04 .mpd
drwxr-xr-x 33 leonardo leonardo   4096 2010-07-23 12:17 Música
-rw-r--r--  1 leonardo leonardo    519 2010-07-10 09:11 .notify-osd
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-08 14:01 .notifyosdconf
-rw-r--r--  1 leonardo leonardo   1170 2010-07-21 12:16 .nvidia-settings-rc
drwxr-xr-x  3 leonardo leonardo   4096 2010-07-07 23:16 .openoffice.org
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-13 16:30 Plantillas
-rw-r--r--  1 leonardo leonardo    675 2010-07-04 20:05 .profile
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-04 20:18 Público
drwx------  2 leonardo leonardo   4096 2010-07-24 11:05 .pulse
-rw-------  1 leonardo leonardo    256 2010-07-04 20:18 .pulse-cookie
drwx------  7 leonardo leonardo   4096 2010-07-23 12:56 .purple
-rw-------  1 leonardo leonardo 263269 2010-07-23 23:39 .recently-used.xbel
-rw-r--r--  1 leonardo leonardo 497781 2010-07-14 16:19 .recently-used.xbel.L64EFV
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-13 16:00 .scripts
drwxr-xr-x  4 leonardo leonardo   4096 2010-07-07 23:29 .shotwell
drwxr-xr-x  3 leonardo leonardo   4096 2010-07-06 19:10 .shutter
-rw-r--r--  1 leonardo leonardo      0 2010-07-04 20:21 .sudo_as_admin_successful
drwxr-xr-x 22 leonardo leonardo   4096 2010-07-23 00:24 .themes
drwx------  4 leonardo leonardo   4096 2010-07-22 21:27 .thumbnails
drwx------  2 leonardo leonardo   4096 2010-07-04 20:19 .update-notifier
drwxr-xr-x  2 leonardo leonardo   4096 2010-07-13 17:17 Vídeos
-rw-------  1 leonardo leonardo  32005 2010-07-24 11:40 .xsession-errors
-rw-------  1 leonardo leonardo 176661 2010-07-23 23:44 .xsession-errors.old
leonardo@ubuntu-desktop:~$ 


```

---

### Post by alfplayer on 2010-07-24
Con bash intentá leer los archivos que no podés leer, primero ir con *cd* a uno de los directorios problemáticos, y después:

*cat archivo*

---

### Post by leonardomdq on 2010-07-24
alfplayer el tema es que no me los reconoce el reproductor que use, no tengo idea como cambiar los privilegios como vienen por default en ubuntu.[U]

[/U]Alguna otra idea?[U]
[/U]

---

### Post by leonardomdq on 2010-07-26
No pude solucionarlo todavia, alguna idea?

Desde ya muchas gracias

---

### Post by alfplayer on 2010-07-26
Se puede cambiar permisos con el comando chmod, pero si podés hacer lo que escribí antes no sería problema de permisos de archivo.

---

### Post by leonardomdq on 2010-07-26
> **alfplayer said:**
> Se puede cambiar permisos con el comando chmod, pero si podés hacer lo que escribí antes no sería problema de permisos de archivo.
Con bash no me permite, me arroja esto:
```

leonardo@ubuntu-desktop:~$ cd /home/leonardo/Música/ACDC - Who Made Who
bash: cd: /home/leonardo/Música/ACDC: No existe el archivo o directorio
leonardo@ubuntu-desktop:~$ 

```
Me hace eso con todos los subdirectorios que estan dentro de la carpeta Música.

---

### Post by alfplayer on 2010-07-26
> **leonardomdq said:**
> Con bash no me permite, me arroja esto:
```

leonardo@ubuntu-desktop:~$ cd /home/leonardo/Música/ACDC - Who Made Who
bash: cd: /home/leonardo/Música/ACDC: No existe el archivo o directorio
leonardo@ubuntu-desktop:~$ 

```
Me hace eso con todos los subdirectorios que estan dentro de la carpeta Música.

No está tomando los espacios (antes y después del guión), se puede arreglar usando comillas simples o dobles:

```
cd "/home/leonardo/Música/ACDC - Who Made Who"
```
o
```
cd '/home/leonardo/Música/ACDC - Who Made Who'
```

---

### Post by leonardomdq on 2010-07-26
Si de esa manera con las comillas me dejo ingresar al directorio. Aclaro que solo me pasa esto con el directorio de Música.

Pero una ves dentro del directorio cuando ejecuto **cat nombre del archivo** no lo reproduce.

Que decis que puede ser?

---

### Post by alfplayer on 2010-07-26
Lo de cat no es para intentar reproducirlo, es para saber si lo puede leer. Si se puede leer debe aparecer en la salida del comando muchísimos símbolos sin significado.

---

### Post by leonardomdq on 2010-07-27
> **alfplayer said:**
> Lo de cat no es para intentar reproducirlo, es para saber si lo puede leer. Si se puede leer debe aparecer en la salida del comando muchísimos símbolos sin significado.
Tal cual salieron muchos simbolos en las carpetas que si me reconoce el reproductor, en las que no me las reconoce cuando ejecute cat no hacia nada.

---

### Post by alfplayer on 2010-07-27
Te recomiendo ejecutar *ls -la* en el directorio que contiene los archivos que no se pueden leer para saber cuál es el problema.

Si se cumplen las dos siguientes condiciones el archivo podría leerse:

Que el usuario dueño del archivo sea el usuario de la sesión de ubuntu:

Ejemplo:
-rw-r--r--  1 **leonardo** leonardo
(el primero de los dos es el usuario dueño, el segundo es el grupo dueño)

y que el permiso de lectura para el usuario esté activado:

Ejemplo:
-**r**w-r--r--  1 leonardo leonardo

(en esa posición debe estar la letra r en negrita, no un guión)

Después si algo no está como debe estar se puede cambiar con chown o chmod (podés buscar información de estos comandos, la opción -R de estos comandos puede ser útil).

---

### Post by Brath-ga on 2010-09-11
A mi me pasa lo mismo.

Tengo una partición llamada Datos del tipo "fusblk", desde la que puedo leer tanto desde Ubuntu como desde XP, pero no puedo compartir ninguna carpeta a pesar de haber utilizado "sudo chown" y "sudo chmod", me sigue indicando que pertenece a root.

Os pongo mi fstab por si está ahí el error:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=1e913f24-464c-4d84-a30d-af3f2fcc59c6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=8b2d818f-9ca0-44b8-b306-d0e84bd9fe5b /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=4c5b0ead-958f-4a0e-b769-8abe009f1303 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Automontar /media/Datos
/dev/sdb4      /media/Datos ntfs-3g default, force 0 0

---

### Post by alfplayer on 2010-09-11
> **Brath-ga said:**
> A mi me pasa lo mismo.

Tengo una partición llamada Datos del tipo "fusblk", desde la que puedo leer tanto desde Ubuntu como desde XP, pero no puedo compartir ninguna carpeta a pesar de haber utilizado "sudo chown" y "sudo chmod", me sigue indicando que pertenece a root.

Os pongo mi fstab por si está ahí el error:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=1e913f24-464c-4d84-a30d-af3f2fcc59c6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=8b2d818f-9ca0-44b8-b306-d0e84bd9fe5b /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=4c5b0ead-958f-4a0e-b769-8abe009f1303 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Automontar /media/Datos
/dev/sdb4      /media/Datos ntfs-3g default, force 0 0

Cómo intentas compartir la carpeta? Con Samba? Con NFS? Cómo?

---

### Post by Brath-ga on 2010-09-11
Es solo para poder acceder a ella desde virtualbox, pero al querer compartir por medio del menú gráfico de propiedades, pone que pertenece a "root" y yo quiero que toda la carpeta pertenezca a "xoan".

sudo chown -R xoan Datos, no produce ningún resultado

---

### Post by alfplayer on 2010-09-11
> **Brath-ga said:**
> Es solo para poder acceder a ella desde virtualbox, pero al querer compartir por medio del menú gráfico de propiedades, pone que pertenece a "root" y yo quiero que toda la carpeta pertenezca a "xoan".

sudo chown -R xoan Datos, no produce ningún resultado

chown y chmod probablemente no funcionan porque es un sistema de archivos NTFS. La solución puede ser con una opción de montaje.

Esto puede ayudar:

de *man mount*

Mount options for ntfs

 uid=value, gid=value and umask=value
              Set the file permission on the filesystem.  The umask  value  is given in octal.  By default, the files are owned by root and not readable by somebody else.

---

### Post by Brath-ga on 2010-09-11
Gracias, seguro que esa es la solución.

Ejecuté blkid y la respuesta a esa unidad fué: /dev/sdb4: LABEL="Datos" UUID="82B46B6FB46B651F" TYPE="ntfs"

Me podrías indicar como quedaría la linea en fstab completa?

Es que no estoy muy "puesto" en ese aopartado y sobre todo en octal.
;)
Gracias

---

### Post by alfplayer on 2010-09-12
Si tu usuario tiene UID 1000 (este no es octal, es el número identificador para el usuario que se crea en la instalación de Ubuntu) puedes probar agregando a esa línea *uid=1000* en la lista separada por coma sin espacios que está en la cuarta columna de fstab.

---

### Post by Brath-ga on 2010-09-12
Gracias de nuevo alfplayer.

Estuve peleandome e informándome todo el dia para poder montarlo con los permisos necesarios y al final dejé esa linea de fstab de esta forma:
```

UUID=82B46B6FB46B651F /media/Datos ntfs-3g uid=1000, gid=1000, umask=007 force 0 0

```
El problema es que si listo los /media con ls -al, me aparece que todo el mundo tiene todos los permisos.
```

drwxr-xr-x  7 root root  4096 2010-09-12 17:32 .
drwxr-xr-x 22 root root  4096 2010-09-12 19:24 ..
drwxr-xr-x  2 root root  4096 2010-09-12 12:18 Cousas_Vellas
drwxrwxrwx  1 xoan root 28672 2010-09-10 13:41 Datos
lrwxrwxrwx  1 root root     7 2010-05-27 09:19 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2010-05-27 09:19 floppy0
drwxr-xr-x  2 root root  4096 2010-09-12 12:18 w2000
drwxr-xr-x  2 root root  4096 2010-09-12 12:18 wxp

```
Los permisos no tendrían que quedar como 770 debido al umask ?

---

### Post by alfplayer on 2010-09-12
Te recomiendo quitar los espacios de la cuarta columna (la columna de las opciones), separando por comas **sin espacios**. Puedes probar quitando la opción umask, si VirtualBox funciona así no habría que hacer nada más. Que quede con permisos para "otros" no sería un problema serio.

---

### Post by Brath-ga on 2010-09-12
Perfecto.
Al quitar los espacios, me permite colocar los permisos que yo quiera sin ser "root".
Gracias y una abrazo.

---

### Post by alfplayer on 2010-09-12
De nada.

---

