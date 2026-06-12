---
title: "Imprimir con Wine"
date: 2009-11-03
forum: Software
---

### Post by aledruetta on 2009-11-03
Hola Comunidad!

Instalé Karmic en una portátil HP Pavilion dv6640br (AMD AthlonX2 - NVidia). Como la dueña está haciendo su primer incursión en GNU/Linux, instalé Wine, Play on Linux y MSOffice 2007. Renegué un poco, pero lo conseguí, y ahora, la susodicha está editando sus documentos .docx.

El problema es que quiso imprimir y no fue posible. Abre una ventana que dice:
```
No existen impresoras instaladas. Para obtener informaciones sobre como instalar 
una impresora, clique en "mostrar ayuda".
```
Y ahí explica el procedimiento que debería realizarse en Windows para instalar una impresora y colocarla como predeterminada.

La impresora está instalada y funcionando a la perfección con aplicaciones de Ubuntu.

¿Alguien tiene una pista para proporcionarme?

Gracias.

---

### Post by josecuervo86 on 2009-11-03
Hola ale, mirate esto: [http://www.kitiara.org/Lists-Archives/l-linux-0203/msg00379.html](http://www.kitiara.org/Lists-Archives/l-linux-0203/msg00379.html)

---

### Post by aledruetta on 2009-11-04
> **josecuervo86 said:**
> Hola ale, mirate esto: [http://www.kitiara.org/Lists-Archives/l-linux-0203/msg00379.html](http://www.kitiara.org/Lists-Archives/l-linux-0203/msg00379.html)

Ups!!! Compleja la cosa... Bueno, gracias, lo voy a investigar y veo si consigo resolverlo.

Saludos.

---

### Post by aledruetta on 2009-11-04
Bueno, ahí estuve mirando un poco... bastante perdido... 

[HTML]Primero instale el CUPS (www.cups.org) para administrar mis impresiones.- 
Lo configure para que imprima en una HP laserJet 2100c que esta en una red 
Windows , dandole como nombre a mi impresora "impresora" .-
Lo probe ..

lp -Pimpresora test.ps produces output
 
Una vez que mi Linux imprimio sin problemas , lei BASTANTE la documentacion 
de Como Imprimir desde Wine.-[/HTML]

En el caso que estoy comentando, con las aplicaciones de Ubuntu no hay problemas. Imprimen a la perfección.

[HTML]  -  Baje los sources del codeweaver para utilizar los utilitarios que vienen 
con &#65533;l .-

   Despues de instalar de vuelta el Wine ,  edite del .wine/config 
agragando lo siguiente :

[spooler]
"FILE:" = "tmp.ps"
"LPT1:" = "|lp -Pimpresora"
[/HTML]

Bajé los sources del codeweaver, pero...

En .wine no existe ningún fichero config. Y los ficheros que hay, no hacen ninguna mención a "[spooler]" ni a "impresora".

Así que, ahí me trabé.

Alguna idea?

---

### Post by josecuervo86 on 2009-11-04
Ale, pero no sera un archivo de configuración? te digo porque según la data hace referencia a la modificación de un archivo. Mira, acá encontré otro que básicamente hace lo mismo: [http://preguntaslinux.org/archive/index.php/thread-3311.html](http://preguntaslinux.org/archive/index.php/thread-3311.html)

---

### Post by aledruetta on 2009-11-05
> **josecuervo86 said:**
> Ale, pero no sera un archivo de configuración? te digo porque según la data hace referencia a la modificación de un archivo. Mira, acá encontré otro que básicamente hace lo mismo: [http://preguntaslinux.org/archive/index.php/thread-3311.html](http://preguntaslinux.org/archive/index.php/thread-3311.html)

Sí, el problema es cuál archivo de configuración, porque en el directorio .wine de esta máquina no está ese archivo config que mencionan en los dos post:
```
patricia@patricia-laptop:~$ ls -al .wine
total 616
drwxr-xr-x  4 patricia patricia   4096 2009-11-03 21:36 .
drwxr-xr-x 62 patricia patricia   4096 2009-11-05 11:59 ..
drwxr-xr-x  2 patricia patricia   4096 2009-11-02 23:20 dosdevices
drwxr-xr-x  4 patricia patricia   4096 2009-11-02 23:15 drive_c
-rw-r--r--  1 patricia patricia 569676 2009-11-03 21:36 system.reg
-rw-r--r--  1 patricia patricia     11 2009-11-03 11:22 .update-timestamp
-rw-r--r--  1 patricia patricia   2584 2009-11-03 21:35 userdef.reg
-rw-r--r--  1 patricia patricia  30348 2009-11-03 21:36 user.reg

```

y dentro de esos archivos que sí están, realicé una búsqueda por "[spooler]" e "impresora", y no aparece nada.

Quizá es porque la versión de wine que tengo es la última, y a la que están haciendo referencia ellos no?

---

### Post by Mauro22 on 2009-11-05
Y si lo creas de una?

Por ahi no está porque ningun programa hizo que wine lo cree.

---

