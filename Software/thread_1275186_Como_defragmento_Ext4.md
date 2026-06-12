---
title: "Como defragmento Ext4?"
date: 2009-09-25
forum: Software
---

### Post by alehawk on 2009-09-25
Hola, estuve leyendo dobre el e4defrag y no entendi anda.
La realidad es que hace poco que estoy en Linux y sobre teste tema encontre 2 urls:
[http://www.kernel.org/pub/linux/kernel/people/tytso/ext4-patches/2.6.28-ext4-3/broken-out/defrag-09-online-defrag-command](http://www.kernel.org/pub/linux/kernel/people/tytso/ext4-patches/2.6.28-ext4-3/broken-out/defrag-09-online-defrag-command)

y

[http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)

Supuestamente en la segundo te explican como preparar toda para dejar listo para usar el defragmentador pero como habla de varios patches, no dice de donde bajarlos, etc, no tengo idea de que hacer.

Mi intencion no es polemizar sobre si el fs se fragmenta o no, quisiera, los que saben, que me den una mano para dejar el e4defrag como para usarse y de paso aprender.
Saludos y gracias!

---

### Post by cgroza on 2009-09-25
You dont need to defragment....

---

### Post by Hei Ku on 2009-09-25
> **alehawk said:**
> Hola, estuve leyendo dobre el e4defrag y no entendi anda.
La realidad es que hace poco que estoy en Linux y sobre teste tema encontre 2 urls:
[http://www.kernel.org/pub/linux/kernel/people/tytso/ext4-patches/2.6.28-ext4-3/broken-out/defrag-09-online-defrag-command](http://www.kernel.org/pub/linux/kernel/people/tytso/ext4-patches/2.6.28-ext4-3/broken-out/defrag-09-online-defrag-command)

y

[http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)

Supuestamente en la segundo te explican como preparar toda para dejar listo para usar el defragmentador pero como habla de varios patches, no dice de donde bajarlos, etc, no tengo idea de que hacer.

Mi intencion no es polemizar sobre si el fs se fragmenta o no, quisiera, los que saben, que me den una mano para dejar el e4defrag como para usarse y de paso aprender.
Saludos y gracias!

El desfragmentador de ext4 esta en estado experimental. Igual, el nivel de fragmentacion que podes tener en una pc normal es mínimo. Normalmente, el filesystem se desfragmenta solo, por su mismo diseño, no como FAT o NTFS. En algunos casos, con servidores de un uso muy intensivo, puede ser necesario desfragmentarlo, pero no es una situacion que veas normalmente.

No es una respuesta filosofica. Si lees cómo es el diseño del filesystem, vas a ver las diferencias respecto a otros que sí se fragmentan.

---

### Post by emiliano_raso on 2009-09-25
Sabía que no es necesario el desfragmentado, pero lo que dijiste me deja pensando porque:
Esas comprobaciones de disco que hace cada X reinicios (que por cierto nunca me fije como programarlas) creia que eran como seudo-desfragmentaciones.

Que son entonces?

---

### Post by Hei Ku on 2009-09-25
Chequeos de integridad. 
Comprueban que las referencias de los inodes y demas elementos del filesystem esten en buen estado. Muy distinto a lo que es una desfragmentacion.

---

### Post by alehawk on 2009-09-25
Gracias pro las resupestas, pero pregunto, con bases de datos pro ejemplo, las bases de datos crecen dia a dia, o sea, yo tnego mi base de datos, le meto un archivo nuevo a la pc, ese archivo no va a continuacion del anterior? De ser asi, si fragmentaria.
En el caso del link que puse el tipo dice que la herramietna la hicieron los que diseñaron el ext4. No es que si o si necesite defragmentar la PC ahora pero siempr es bueno saber como hacerlo :)

---

### Post by staar on 2009-09-25
> **alehawk said:**
> Gracias pro las resupestas, pero pregunto, con bases de datos pro ejemplo, las bases de datos crecen dia a dia, o sea, yo tnego mi base de datos, le meto un archivo nuevo a la pc, ese archivo no va a continuacion del anterior? De ser asi, si fragmentaria.
En el caso del link que puse el tipo dice que la herramietna la hicieron los que diseñaron el ext4. No es que si o si necesite defragmentar la PC ahora pero siempr es bueno saber como hacerlo :)

ext4 no es tan simple (en realidad, ningún filesystem lo es), es un sistema mucho más complicado, los archivos no se agregan siempre "a continuación del anterior", una explicación técnica de como funciona sería muy larga para ponerla acá (y tampoco está a mi alcance desarrollarla), pero lo importante es que ext4 está bien hecho, y para uso de una pc de escritorio no es necesario desfragmentar, porque el filesystem NO se fragmenta significativamente, otro caso, como explicó Hei Ku, es si lo tuyo es un servidor con uso muy intensivo...

no existe una explicación detallada para novatos de como usar e4defrag justamente por eso, porque no es necesario para el usuario medio utilizar esa herramienta (que incluso está en estado experimental aún)...

saludos

---

### Post by Hei Ku on 2009-09-25
Acá hay un articulo en ingles que hace una breve comparacion entre filesystems y te da el comando para ver la fragmentación que tenés. En general, debajo del 10% estás tranquilo.

[http://www.itworld.com/nls_unixfrag040929](http://www.itworld.com/nls_unixfrag040929)

---

### Post by pablo.s on 2009-09-25
Para explicarlo de una
manera muuuy simple:
Hay dos formas básicas
que utilizan los sistemas 
de archivos para escribir
los datos:
**-Por Bloques**
Usa el espacio de forma
minima para guardar espacio
en disco. Cuando escribe
información nueva, utiliza el
bloque libre más próximo,
con lo que se escribe por lo
general al azar. Si te vino a
la cabeza FAT, bingo.
**-Por Medida**
Usa el espacio en bloques
grandes, reservando de
forma secuencial (uno detrás
de otro) los bloques. Por esto
mismo, la fragmentación es
mínima. Si pensaste en Ext3/4,
ReiserFS, ZFS, estás en lo
cierto.

---

### Post by alehawk on 2009-09-26
Gracias por la data, incluso ejecutando el fsck me tiro que tengo algun despelote de inodes asi que lo voy a reparar...
De apoco me voy desayunando con esto del linux.

---

### Post by alehawk on 2009-09-26
Bueno, quise hacer el fsck del /dev/sda5 boteando desde el cd de ubuntu y no hubo caso, em edcia qu eno tenia problemas, lo monte y me mostraba cualquier cosa, como si hubiese montado el sda1 (/boot).
Vuelvo a bootear normal el sistema y me sigue diciendo que hay errores en el sistema :S
Cosa rara, jamas me paso de montar algo y que me muestre cualquiera...

---

