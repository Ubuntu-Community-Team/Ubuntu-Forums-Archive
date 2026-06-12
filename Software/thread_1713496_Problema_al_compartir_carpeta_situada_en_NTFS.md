---
title: "Problema al compartir carpeta situada en NTFS"
date: 2011-03-24
forum: Software
---

### Post by Dolph-Flynn on 2011-03-24
Hola a todos,

Aunque lo mio con Linux lleva siendo un querer y no poder desde la época en que salió la primera Red Hat, por fin me he decidido y hace ya unos meses que he decidido usar únicamente este maravilloso sistema y olvidarme de nuestro "querido" windows.
En casa no he tenido problemas y tengo un portátil funcionando exclusivamente con Ubuntu 10.04 a la perfección, también una máquina fija con varias particiones y SO instalados (mi hijo también se está pasando a linux, aunque he tenido que virtualizarle un XP con virtualbox por los problemas existentes con el famoso iTunes, y también hasta que se acostumbre al Gimp en lugar del Photochop).

El siguiente paso ha sido instalarlo en el trabajo, donde tengo algún portátil conectado vía inalámbrica, más dos máquinas fijas con windows XP sp3 y mi equipo donde tengo instalada en una partición Win7 y en la otra Ubuntu 10.04 con el kernel 2.6.32-30-generic-pae (además de alguna partición para datos).

Esta es la salida de fdisk:

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xa5db015f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2              13       12704   101941456    7  HPFS/NTFS
/dev/sda3           12705      121601   874714113    f  W95 Ext'd (LBA)
La partición 3 no termina en un límite de cilindro.
_**/dev/sda5           25498      121601   771950592    7  HPFS/NTFS**_
/dev/sda6           13705       25498    94726144   83  Linux
/dev/sda7           12705       13705     8036352   82  Linux swap / Solaris


El equipo está conectado a internet, a una impresora de red y dentro de un grupo de trabajo donde también están los otros equipos Win. Instalé samba y he probado a configurarlo de múltiples formas, la última editando a mano el smb.conf. He leído todo lo que he podido sobre el tema y, o no he buscado bien, o no encuentro la solución.

Al grano, el tema es el siguiente: Todos los equipos se ven entre si. Si creo una carpeta en mi /home y la comparto, no tengo problemas de ningún tipo, puedo asignarle permisos, los otros equipos la ven y pueden acceder, es decir, todo OK.

El problema viene cuando quiero compartir una carpeta que ya existía (en la partición donde guardaba los datos en win: **sda5**). Si lo hago desde nautilus unas veces me la da como compartida y otras veces ni siquiera eso, aún cuando me la da como compartida NO PUEDO CAMBIAR los permisos a esa carpeta. Si lo hago desde consola como root ¡no me hace ni caso!!!.
He probado a crear una carpeta nueva en esa misma partición por si se tratara de alguna cuestión de permisos heredados de win, y... tampoco.

Alguna idea???

Gracias por anticipado.

______________________________


:(:(:(:(

Me contesto a mi mismo.... (glups) quizás me he anticipado pero... resulta que llevo tres días tratando de encontrar la solución (en español, porque no domino mucho el inglés) y se me ha ocurrido buscar con la cadena "shared folder on ntfs doesn't work" y me he encontrado con este hilo: [http://ubuntuforums.org/showthread.php?t=1586804](http://ubuntuforums.org/showthread.php?t=1586804)

Donde, viene "perfectamente" explicado.... y encima funciona !!!

Pues eso, que lo siento si me he anticipado.

Un saludo a todos. :P

---

