---
title: "como se usa gcc"
date: 2008-06-13
forum: Software
---

### Post by phxnd on 2008-06-13
eso "nomas",,,,como se usa gcc :O para compilar un programa en C por ejemplo...como hago?

---

### Post by cwaidelich on 2008-06-13
> **phxnd said:**
> eso "nomas",,,,como se usa gcc :O para compilar un programa en C por ejemplo...como hago?

Translation: 
How to use gcc? How to compile a program in C?

---

### Post by faktorqm on 2008-06-14
cwaidelich: En este foro se habla español, y nadie te pidio una traduccion, pregunto como se usa el gcc. Lee bien antes de contestar.

---

### Post by tzulberti on 2008-06-14
Hola. Para una compilacion de un archivo, como el holaMundo, podrias hacer lo siguiente:
gcc -o "nombreEjecutable" nombreArchivo.c

Por ejemplo: gcc -o holaMundo holaMundo.c. Esto va a crear un ejecutable llamado holaMundo a partir del archivo holaMundo.c. Para ejecutarlo vas a tener que escribir en una consola: ./holaMundo.

De todas formas aca tenes un ejemplo un poco mas practico sobre como hacer para compiarlo cuando los archivos tenes mas de un archivo en el programa:
[http://tldp.org/HOWTO/Program-Library-HOWTO/more-examples.html](http://tldp.org/HOWTO/Program-Library-HOWTO/more-examples.html)

---

### Post by phxnd on 2008-06-15
> **tzulberti said:**
> Hola. Para una compilacion de un archivo, como el holaMundo, podrias hacer lo siguiente:
gcc -o "nombreEjecutable" nombreArchivo.c

Por ejemplo: gcc -o holaMundo holaMundo.c. Esto va a crear un ejecutable llamado holaMundo a partir del archivo holaMundo.c. Para ejecutarlo vas a tener que escribir en una consola: ./holaMundo.

De todas formas aca tenes un ejemplo un poco mas practico sobre como hacer para compiarlo cuando los archivos tenes mas de un archivo en el programa:
[http://tldp.org/HOWTO/Program-Library-HOWTO/more-examples.html](http://tldp.org/HOWTO/Program-Library-HOWTO/more-examples.html)

entonces el gcc no tiene una interfaz grafica donde te muestre de forma linda  las cosas de colores? jaja

---

### Post by francoel69 on 2008-06-16
> **phxnd said:**
> entonces el gcc no tiene una interfaz grafica donde te muestre de forma linda  las cosas de colores? jaja

La verdad que no. Siendo usuario de un UNIX en general te vas a tener que acostumbrar un poco al uso de la consola. Igual no es dificil el uso del gcc, como dijeron antes. Un truco es el uso de Makefiles. Instalate el make: `sudo apt-get install make' y despues hace lo siguiente: parate en donde este tu .c (o .cpp) y pone: make <nombre>, donde <nombre> es el nombre del archivo .c dond este el ejecutable, y todo se hace solo, con algunas opciones por defecto del Make. Por ejemplo: si tenes un archivo en C llamado main.c donde esta el main, despues hace make main y listo (sin la necesidad de tener un archivo Makefile). (Un truco para compilar y ejecutar a continuacion es: make main && ./main). Despues de compilar corre tu programita con ./<nombre>. Espero que te haya servido esta mini ayudita.

---

### Post by sdennie on 2008-06-16
Tambien podes usar un IDE como Anjunta si no te gusta la consola.  Nunca lo use yo pero es muy conocido:

```

sudo apt-get install anjunta autogen

```

---

### Post by phxnd on 2008-06-16
> **francoel69 said:**
> La verdad que no. Siendo usuario de un UNIX en general te vas a tener que acostumbrar un poco al uso de la consola. Igual no es dificil el uso del gcc, como dijeron antes. Un truco es el uso de Makefiles. Instalate el make: `sudo apt-get install make' y despues hace lo siguiente: parate en donde este tu .c (o .cpp) y pone: make <nombre>, donde <nombre> es el nombre del archivo .c dond este el ejecutable, y todo se hace solo, con algunas opciones por defecto del Make. Por ejemplo: si tenes un archivo en C llamado main.c donde esta el main, despues hace make main y listo (sin la necesidad de tener un archivo Makefile). (Un truco para compilar y ejecutar a continuacion es: make main && ./main). Despues de compilar corre tu programita con ./<nombre>. Espero que te haya servido esta mini ayudita.
buenisimo(Y) gracias


> **vor said:**
> Tambien podes usar un IDE como Anjunta si no te gusta la consola.  Nunca lo use yo pero es muy conocido:

```

sudo apt-get install anjunta autogen

```

no tengo que agregar algun repositorio? anjunta no ta xD

---

### Post by sdennie on 2008-06-16
> **phxnd said:**
> buenisimo(Y) gracias




no tengo que agregar algun repositorio? anjunta no ta xD

Me equivoqué:

```

sudo apt-get install anjuta autogen

```

---

### Post by tzulberti on 2008-06-16
> **vor said:**
> Me equivoqué:

```

sudo apt-get install anjuta autogen

```

Perdon, pero que el anjunta es demasiado pesado para hacer aplicaciones simples... Te para empezar te recomiendo uno llamado geany.

---

### Post by gefarion on 2008-06-17
Te recomiendo Code::Blocks se instala muy facil en Ubuntu, y es muy facil de usar y muy completo.

[http://www.codeblocks.org/](http://www.codeblocks.org/)

saludos.

---

### Post by Hei Ku on 2008-06-17
Si es en c++, podes usar KDevelop, es bastante completo.
Y el rey de todos creo que es el Eclipse, al que le agregas el plugin para c/c++

---

### Post by tzulberti on 2008-06-17
> **Hei Ku said:**
> Si es en c++, podes usar KDevelop, es bastante completo.
Y el rey de todos creo que es el Eclipse, al que le agregas el plugin para c/c++

El plugin de C++ para eclipse se llama CDT y se puede instalar usando usando apt-get. Sin embargo, no funciona tan bien como la version de java (por lo menos en la version que habia probado hace un año). 

Ademas, el eclipse me parece un poco demasiado pesado para hacer tps de la facultad o para estar empezando.

---

### Post by obernhardt on 2011-10-24
> **sdennie said:**
> Tambien podes usar un IDE como Anjunta si no te gusta la consola.  Nunca lo use yo pero es muy conocido:

```

sudo apt-get install anjunta autogen

```
  es anjuta, no anjunta

---

