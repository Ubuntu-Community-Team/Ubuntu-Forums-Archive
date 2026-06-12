---
title: "caracteres raros en nombres de archivo/carpeta"
date: 2008-07-30
forum: Software
---

### Post by sergiom99 on 2008-07-30
Hola gente, cada vez que descomprimo un rar en el Kubuntu, los archivos que tienen acentos, ñ's, etc, me quedan como los del primer snap.
 [[IMG]http://img152.imagevenue.com/loc985/th_90262_snap3_122_985lo.jpg[/IMG]](http://img152.imagevenue.com/img.php?image=90262_snap3_122_985lo.jpg)

Los del segundo snap son bajados desde la desktop con XP, ya descomprimidos  y la ñ se ve perfecto. Los acentos tambien.
(la mula la tengo andando en esa PC)
 [[IMG]http://img102.imagevenue.com/loc438/th_90267_snap4_122_438lo.jpg[/IMG]](http://img102.imagevenue.com/img.php?image=90267_snap4_122_438lo.jpg)

sospecho que tiene algo que ver con el fstab, puede ser?
aca lo posteo por las dudas si hay que corregir algo.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=68124ed6-880b-403b-bbf6-2aa534971b79 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c3aa61e4-b3ea-418a-b4bb-d73ca1e50b02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

espero poder arreglarlo, porque la verdad corregir todos los nombres a mano es un bajon!!
saludos/ Sergio

---

### Post by Hei Ku on 2008-07-30
Fijate que tengas instalados todos los locale necesarios. Eso es porque esta usando caracteres Unicode que aparentemente no tenes instalados.

---

### Post by sergiom99 on 2008-07-30
tirame un metro mas de soga please. donde los miro? si falta algo como lo instalo? 
apt-get install <<what!>>?

Gracias Hei Ku!

---

### Post by Hei Ku on 2008-07-30
yo vi un caso parecido con una instalación que la habían hecho en inglés, y no le habían instalados los archivos para español.
Busca en Synaptic los paquetes de lenguaje, como language-pack-es
Probablemente no sea eso, pero más vale fijarse.

Con qué programa lo estas descomprimiendo? Usas el rar free o non-free?

---

### Post by sergiom99 on 2008-07-30
esta tarde llego a casa y me fijo ambas cosas.
que diferencia hay entre los dos rar?

Gracias capo, siempre un gusto.

---

### Post by Hei Ku on 2008-07-30
el non-free tiene ciertas capacidades extras, pero esta "envenenado" con patentes, por eso no es libre realmente. 

Funciona mejor, pero a costa de tu libertad. ;)

---

### Post by sergiom99 on 2008-07-31
tenía el unrar-free y tengo todos los language-pack-es (base, KDE, etc.)

Alguna otra tip?
Gracias!

---

### Post by faktorqm on 2008-08-02
Mirá, hasta lo que yo entiendo depende del que comprime. 

```

-sc<charset>[objects]

Specify the character set for list files and archive comment files.

'Charset' parameter is mandatory and can have one of the following values:

U - Unicode;
A - ANSI (Windows) encoding. Windows version only;
O - OEM (DOS) encoding. Windows version only.

Files in Unicode format must have FFFE or FEFF Unicode character in the beginning, otherwise RAR will ignore this switch and process the file as ASCII text.

'Objects' parameter is optional and can have one of the following values:

L - list files;
C - comment files.

It is allowed to specify more than one object, for example, -scolc. If 'objects' parameter is missing, 'charset' is applied to all objects.

This switch allows to specify the character set for files in -z[file] switch, list files and comment files written by "cw" command.

Examples:

1) rar a -scol data @list

Read names contained in 'list' using OEM encoding.

2) rar c -scuc -zcomment.txt data

Read comment.txt as Unicode file.

3) rar cw -scuc data comment.txt

Write comment.txt as Unicode file.

```

Esto significa:

```

-sc<charset>[objects]

Especfica el juego de caracteres en la lista de archivo y en los comentarios.

El parámetro 'Charset' es olbligatorio y puede tener alguno de estos valores:

U - Unicode;
A - Codificación ANSI (Windows). Sólo válido en la versión de rar para Windows.
O - Codificación OEM (DOS). Sólo válido en la versión de rar para Windows.

Los archivos en formato Unicode deben tener el caracter Unicode FFFE o FEFF en el comienzo, de lo contrario, RAR ignorará este modificador (se refiere al -sc) y procesará el archivo como texto ASCII.

El parámetro 'Objects' es opcional y puede tener alguno de los siguientes valores:

L - se refiere a los nombres de los archivos;
C - se refiere al archivo de comentarios.

Esto te permite especificar más de un objeto, por ejemplo, -scolc. Si el parámetro 'objects' no está, 'charset' es aplicado a todo.

Este modificador permite especificar el conjunto de caracteres en archivos con el modificador -z[file], en los nombres de los archivos y en los archivos de comentarios escritos con el comando "cw".

Ejemplos:

1) rar a -scol data @list

Lee los nombres contenidos en 'list' utilizando la codificación OEM. 

2) rar c -scuc -zcomment.txt data

Lee el archivo comment.txt utilizando la codificación Unicode.

3) rar cw -scuc data comment.txt

Escribe el archivo comment.txt utilizando la codificación Unicode.

```

Bueno, aunque no resolví el problema, intenté esclarecer el motivo. Salu2!!

---

### Post by sergiom99 on 2008-08-02
Lo voy a tener en cuenta si comprimo yo los archivos. Aunque generalmente lo hago con el winrar y no por CLI.
Gracias!

---

