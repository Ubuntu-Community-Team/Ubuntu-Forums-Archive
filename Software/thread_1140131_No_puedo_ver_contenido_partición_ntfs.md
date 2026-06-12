---
title: "No puedo ver contenido partición ntfs"
date: 2009-04-27
forum: Software
---

### Post by aledruetta on 2009-04-27
Hola Comunidad! 
 
Les comento cuál es mi problema:  
 
Tengo instalado Vista en una partición y Ubuntu 9.04 en otra. La instalación de Ubuntu la hice en una partición ext4 y otra Swap. No elegí la opción de migrar de Windows en el momento de la instalación de Ubuntu. 
 
Cuando quiero acceder a algún documento de Windows, veo que la partición está montada. Puedo llegar hasta un cierto nivel de carpetas en el árbol de Windows, pero no puedo ver, ni mucho menos ejecutar o abrir, ningún archivo. 
 
Por ejemplo: navegando, llego hasta Mis Documentos. Adentro yo sé que hay carpetas, pero no puedo verlas. Es como si dentro de Mis Documentos no hubiese absolutamente nada. 
 
Tengo también, un disco USB externo. Sin embargo con ese disco no tengo problemas. 
 
¿Cómo podría resolver esto? 
 
Gracias, 
Hasta pronto!

---

### Post by aledruetta on 2009-04-27
[SIZE=2]Buscando y buscando, siguiendo distintos tutoriales, etc., fui intentando lo que sigue a continuación: 
 
Ejecuto en terminal: 

[/SIZE]       [SIZE=2]Código:[/SIZE]              [SIZE=2]root@alejandro-laptop:/media# ls -l[/SIZE]    [SIZE=2] 

Me da como resultado: 

[/SIZE][SIZE=2]total 15 
lrwxrwxrwx 1 root root     6 2009-04-24 20:22 cdrom -> cdrom0 
dr-xr-xr-x 1 root root  2856 2006-04-20 22:28 cdrom0 
drwxrwxrwx 1 root root 12288 2009-04-25 15:14 disk[/SIZE]    [SIZE=2] 

Intenté cambiar los privilegios: 

[/SIZE][SIZE=2]root@alejandro-laptop:/media# chmode -R 777 disk 
root@alejandro-laptop:/media# chmod -R a+rwx disk/[/SIZE]    [SIZE=2] 

Instalé los paquetes: 

[/SIZE][SIZE=2]root@alejandro-laptop:/media# aptitude install ntfs-3g 
root@alejandro-laptop:/media# aptitude install ntfs-config[/SIZE]    [SIZE=2] 

Y nada. 

Abrí Nautilus como root: 

[/SIZE][SIZE=2]root@alejandro-laptop:/media# nautilus[/SIZE]    [SIZE=2] 

Intenté cambiar desde ahí los privilegios y cuando selecciono algo distinto, automáticamente vuelve a donde estaba antes. No respeta lo que seleccioné. 

También intenté cambiar el propietario con el comando: 

[/SIZE][SIZE=2]root@alejandro-laptop:/media# chow usuario:usuario disk[/SIZE]    [SIZE=2] 
 
En fin, no sé qué hacer. 
¿Alguien sabe? ¿Alguien puede darme una mano? 
 
Saludos, 
El Aleph[/SIZE]

---

### Post by gmunioz on 2009-04-27
Hola ale...:

1- Los sistemas de archivos de Microsoft, no poseen ni conocen los permisos

de los sistemas de archivos Linux.

2- Los permisos los debes otorgar al directorio donde se monta el sistema 

de archivos de Microsoft en forma recursiva.

3- Previo a otorgar los permisos, debe desmontarse el sistema de archivos

de Microsoft.

El procedimiento sería entonces:

a- Desmontar el sistema de archivos

b- Ejecutar la orden en consola:

sudo chmod -Rf 777 /media/disk

c- Instalados ntfs-3g, fuse-utils, ntfsprogs y ntfs-config, desde:

Aplicaciones - Herramientas de sistema - Herramienta de configuracion 

NTFS - activar el soporte para escritura en los dispositivos

Saludos.

---

### Post by aledruetta on 2009-04-27
Hola gmunioz,

Muy amable por tu atención. Te cuento cómo me fue:

Instalé los paquetes que me indicaste:

```
root@alejandro-laptop:~# aptitude install ntfs-3g fuse-utils ntfsprogs ntfs-config
```Desmonté la partición de Windows:

```
root@alejandro-laptop:~# umount /media/disk
```Ejecuté chmod:

```
root@alejandro-laptop:~# chmod -Rf 777 /media/disk
```Y sigo sin poder ver los archivos dentro de las carpetas, sobre todo en la carpeta Mis Documentos, que es a lo que más me interesaría acceder.

Además, en Aplicación --> Herramientas del Sistema, no aparece Herramientas de Configuración NTFS

Intenté con:

```
root@alejandro-laptop:~# ntfs-config
```Y ahí sí, se abrió la ventana, me pidió que le asigne un nombre a la partición (la renombré como Windows) y se habilitó el soporte de escritura de discos externos e internos. Pero, seguía sin poder ver los archivos.
De casualidad encontré la Herramienta de Configuración NTFS en Sistema --> Administración. Todo seguía igual.

Desmonté:

```
root@alejandro-laptop:~# umount /media/Windows
```Y volví a ejecutar:

```
root@alejandro-laptop:~# chmod -Rf 777 /media/Windows
```Monté: 

```
root@alejandro-laptop:~# mount /media/Windows
```Y nada, sigo sin poder acceder a los archivos.


[SIZE=2]**¿Hice algo errado? ¿Se te ocurre algo más?**[/SIZE]

Saludos,
Alejandro.

---

### Post by aledruetta on 2009-04-27
Disculpame, ya lo conseguí. El problema es que no me daba cuenta que hay una carpeta Document and Settings y otra Users. Yo quería entrar en Document and Settings y, no sé por qué, pero los documentos están en Users.

Bueno, te agradesco la ayuda,
Un abrazo,
Alejandro.

---

### Post by Usul Muhadiv on 2010-01-25
Yo estaba cometiendo el mismo error, hay ke tener cuidado con WVista y WSeven con este tema.

Gracias por la ayuda, 
Saludos Cordiales

---

