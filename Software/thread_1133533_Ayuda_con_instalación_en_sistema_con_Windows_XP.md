---
title: "Ayuda con instalación en sistema con Windows XP"
date: 2009-04-23
forum: Software
---

### Post by -JuanmA- on 2009-04-23
Hola a todos desde hace tiempo me entró curiosidad por incursionar en el mundo Linux y nunca me decidí a hacerlo hasta ahora.
Me bajé la versión 8.10 de Ubuntu y la estuve probando mediante el Live CD, pero cuando me decidí a instalar definitivamente, aparecieron los problemas.

Detallo mi PC:
AMD Phenom 8650 Triple-Core 2.31 Ghz
2 GB RAM
Disco SATA II 320 gb --> Particiones C (Windows), D (NTFS) y E (NTFS)
Disco SATA II 500 gb --> Particiones F (NTFS) y G (NTFS) + 100 gb libres que quiero destinar a Ubuntu

Inicio desde el LiveCD y elijo la opción Instalar. Luego de setear idioma, teclado, etc llego a la parte del particionado del disco y elijo manual.

El primer problema se me dio cuando quise crear en el espacio libre una partición para / de 15 gb, otra para la swap de 2gb y otra para /home con los 83 gb restantes. 

Cree la primera partición de 15 gb como Primaria y sistema de archivos ext3 con punto de montaje en /.
Pero después cuando quiero crear las otras dos, al seleccionar "Nueva Partición" en el espacio libre no me dio la opción a elegir entre Primaria o Lógica. 
Seleccioné directamente los 83gb, ext3 y montaje en /home y me llevé la sorpresa de que los 2 gb que iba a usar para la swap me aparecen como "espacio inútil" o algo por el estilo.
Leyendo en algunos foros encontré que esto se debe a que no se pueden crear más de cuatro particiones primarias en un disco y que entonces creara una partición primaria para / y una partición extendida donde a su vez crearía dos lógicas, una para /home y otra para la swap. ¿Entendí bien? Si es así creo que no supe como hacerlo. 

Entonces deshice todo y empecé de nuevo, solo que esta vez cree primero una partición de 2gb para la swap (pude seleccionar entre lógica o primaria y elegí lógica), luego una de 83 gb con sistema ext3 pero sin seleccionar un punto de montaje (también elegí lógica) y luego otra de 15 gb sin seleccionar tampoco un punto de montaje (como primaria). O sea, de esta forma sí pude elegir entre Primarias o Lógicas. Luego edité las dos últimas particiones, en la primera seleccioné /home como punto de montaje y en la segunda seleccioné /.
Es decir, supuestamente logré hacer lo que leí en todos lados que tenía que hacer para poder comenzar con la instalación.
Cuando procedo a instalar, luego de unos minutos me salió el siguiente error:
[I][B]
Falló el intento de montar un sistema de ficheros de tipo ext3 en scsi4(0,0,0), partición #3 (sdb) sobre /.
Puede reanudar el particionado en el menú de partición.[/B]

[/I]Y me da como opciones "Continuar" o "Retroceder" (no recuerdo si era esta la palabra, pero se entiende que se refiere a volver a atrás).

No me animé a continuar así que volví a la parte de las particiones y no supe que más hacer. 

¿En qué me equivoqué? ¿Cuál puede ser la raíz del problema y cómo debería proceder?

Espero se haya entendido todo esto que escribí, intenté ser lo más claro posible teniendo en cuenta que no estoy para nada familiarizado con toda la terminología linuxera.

Desde ya muchas gracias a los que se tomaron la molestia de leer y si me pueden dar una mano les estaré aún más agradecido.

---

### Post by gmunioz on 2009-04-23
Hola jua.....:

Desde una sesión live, pulsa:

Aplicaciones - Accesorios - Terminal

En la consola ejecuta:

sudo fdisk -l

copia y pega la salida en el post.

Para saber que hacen sudo y fdisk

man comando

En la consola.

Saludos.

---

### Post by -JuanmA- on 2009-04-23
Gracias por contestar gmunioz, acá pego lo que me mostro el fdisk:

Disco /dev/sda: 320.0 GB, 320072933376 bytes
16 cabezas, 63 sectores/pista, 620181 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes
Identificador de disco: 0xdcebdceb

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       62415    31457128+   7  HPFS/NTFS
/dev/sda2           62416      620180   281113560    f  W95 Ext'd (LBA)
/dev/sda5           62416      312076   125829112+   7  HPFS/NTFS
/dev/sda6          312077      620180   155284384+   7  HPFS/NTFS

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x9799d9fe

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       13055   104857672+   7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sdb2           13055       58934   368529620    f  W95 Ext'd (LBA)
/dev/sdb3           58935       60801    14996677+  83  Linux
/dev/sdb5           13055       47648   277872808+   7  HPFS/NTFS
/dev/sdb6           47649       47897     2000061   82  Linux swap / Solaris
/dev/sdb7           47898       58934    88654671   83  Linux

---

### Post by staar on 2009-04-23
lo que podes hacer es lo siguiente, agarrá el editor de particiones en el live cd, y creá una partición extendida con todo tu espacio libre, despues, dentro de esta partición, creá las particiones logicas que quieras (las particiones extendidas albergan particiones lógicas, no almacenan datos, osea una partición extendida tiene adentro la cantidad de lógicas que quieras, es para poder tener muchas particiones en un disco)

despues en el instalador selecciona los puntos de montaje correspondientes y listo :-D

saludos

---

### Post by gmunioz on 2009-04-23
Hola jua....:


En el disco donde intentas instalar, se encuentran:

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x9799d9fe

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdb1 1 13055 104857672+ 7 HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sdb2 13055 58934 368529620 f W95 Ext'd (LBA)
/dev/sdb3 58935 60801 14996677+ 83 Linux
/dev/sdb5 13055 47648 277872808+ 7 HPFS/NTFS
/dev/sdb6 47649 47897 2000061 82 Linux swap / Solaris
/dev/sdb7 47898 58934 88654671 83 Linux

Esto implica un serio riesgo de perder toda la información que tienes en el.

Te sugiero que desde el operativo de Microsoft, ejecutes chkdsk /f sobre ambas particiones ntfs, con el fin de reparar los errores.

Luego pongas a salvo el contenido de /dev/sdb5  seguramente G: para Microsoft y desde el gestor de particiones que mas te agrade o sepas usar:

1- Elimines todas las particiones del disco menos /dev/sdb1

2.- Previo ejecutar nuevamente chkdsk /f sobre /dev/sdb1

3- Crees una partición primaria, formato ntfs, para restaurar el contenido de G:, una partición primaria cualquier formato para destinar a / de al menos 15 gigas y en el resto una partición extendida.

4- Ejecutes nuevamente chkdsk /f sobre /dev/sdb1, restaures tus archivos en G:, seguramente /dev/sdb2

5- Instales ubuntu, eleigiendo particionamiento manual al llegar al mismo, e instales en:

Una partición primaria, activa, sistema de archivos ext4 (si usas jaunty) o ext3 (hardy o intrepid) punto de montaje /, de 15 gigas en la primaria creada previamente.

Una partición lógica que se creará en la extendida, sistema de archivos intercambio de 1 giga para swap, montaje por defecto

Una partición lógica que se creará en la extendida, sistema de archivos reiserfs, punto de montaje /home, tamaño de 2 gigas mínimo, en adelante lo que quieras otorgarle según dispongas y necesites. 

Saludos.

---

### Post by -JuanmA- on 2009-04-23
Uh me muero si pierdo todo lo de ese disco. Gracias por la ayuda, ya mismo me pongo a hacer todo lo que me dijiste

Edito: ejecute el chkdsk sobre la partición F y me dio el siguiente resultado:

[IMG]http://img167.imageshack.us/img167/6481/51201644.jpg[/IMG]

Por lo que entiendo no hay ningún problema.

Pero cuando lo quise hacer sobre G me salió lo siguiente:

[IMG]http://img300.imageshack.us/img300/7244/11498787.jpg[/IMG]

A las dos preguntas que me hizo le respondí que NO porque no estaba seguro de hacerlo.

¿Qué debería hacer?

---

### Post by gmunioz on 2009-04-23
Hola jua...:

Si bien esto no tiene nada que ver con Ubuntu y deberías consultarlo en un

foro Microsoft, lo que debes hacer es responder que sí a las preguntas.

Esto es así, porque han quedado abiertos los flags del operativo de 

Microsoft sobre la partición, como si estuviere montada, y al forzarla lo

que haces es cerrarlos. Esto es con la primer opción, la segunda opción lo

que hace es esperar a un nuevo inicio para que sean  desmontados los flags

por el operativo.

Saludos.

---

