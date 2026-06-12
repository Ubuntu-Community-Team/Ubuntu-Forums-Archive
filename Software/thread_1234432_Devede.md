---
title: "Devede"
date: 2009-08-07
forum: Software
---

### Post by andy_91 on 2009-08-07
hola a todos, voy a ser breve.

use el devede ara hacer un svcd (que me tardo casi 3 horas) y cuando termina me aparesen dos archivos uno *.bin y otro *.cue. Al intentar pasarlos a *.iso me tira error
```
andy@andy-desktop:~$ bchunk Software Libre (Trabajo promocion humana).bin Software Libre (Trabajo promocion humana).cue Software Libre (Trabajo promocion humana).iso
bash: error de sintaxis cerca de token no esperado `('
```

alguna idea, es que no quiero estar otras 3 horas, desde ya gracias

PD:Me olvide de ponerlo en la categoria correspondiente, perdon :(

---

### Post by staar on 2009-08-07
una de dos, o le cambias el nombre a uno sin espacios, o le ponés los \ donde van (en la consola se debe poner un \ antes de cada espacio), sería ```
bchunk Software\ Libre\ (Trabajo\ promocion\ humana).bin Software\ Libre\ (Trabajo\ promocion\ humana).cue Software\ Libre\ (Trabajo\ promocion\ humana).iso
``` y, no estoy seguro, pero creo que solo hace falta el .cue (porque este especifica donde está el .bin)

saludos

---

### Post by guillermolisi on 2009-08-07
No le gustan los "()" que le pusiste a los nombres/prefijos de archivos.

Para allanar el camino, renombralos usando "_" en lugar de los espacios, asi no tenes que usar caracteres auxiliares para que "lea" el nombre de archivo completo y no interprete ni espacios ni esos caracteres auxiliares.

Usar "_" en lugar de espacios es otra de las Mejores Practicas aconsejadas. No te resuelve la vida pero te la facilita. :)

---

### Post by andy_91 on 2009-08-09
gracias por los consejos, pero igual no funk, alguna idea :confused:

---

### Post by pablo.s on 2009-08-09
K3B puede grabar los
archivos .cue como
imagenes de disco.
No veo porqué necesitás
pasarlo a .iso.

---

### Post by guillermolisi on 2009-08-09
> **andy_91 said:**
> gracias por los consejos, pero igual no funk, alguna idea :confused:
Algun mensaje de error que oriente algun consejo ?

---

### Post by andy_91 on 2009-08-10
> **pablo.s said:**
> K3B puede grabar los
archivos .cue como
imagenes de disco.
No veo porqué necesitás
pasarlo a .iso.

por que no mezclo librerias qt con gtk y uso xfce (no creo que me corra el k3b 4 con 256MB)
> **guillermolisi said:**
> Algun mensaje de error que oriente algun consejo ?

el mismo no cambia el msj de error

---

### Post by guillermolisi on 2009-08-10
Mostranos como quedo la nueva linea de comando, luego de hacerle las adecuaciones que se sugirieron.

---

### Post by andy_91 on 2009-08-10
ya dije igual que antes ```
bchunk Software\ Libre\ (Trabajo\ promocion\ humana).bin Software\ Libre\ (Trabajo\ promocion\ humana).cue Software\ Libre\ (Trabajo\ promocion\ humana).iso
bash: error de sintaxis cerca de token no esperado `('
```

---

### Post by euzkoarima on 2009-08-11
Parece que no le gusta el paréntesis.
Yo probaría, primero poniendo entre comillas

```
bchunk "Software Libre (Trabajo promocion humana).bin" "Software Libre (Trabajo promocion humana).cue" "Software Libre (Trabajo promocion humana).iso"
```

Y si no funciona, idem pero sin los ( ) en el nombre.

Saludos,
Eduardo

---

### Post by Mister X on 2009-08-11
Para los parentesis tambien necesitas el caracter de escape:
```

bchunk Software\ Libre\ \(Trabajo\ promocion\ humana\).bin Software\ Libre\ \(Trabajo\ promocion\ humana\).cue Software\ Libre\ \(Trabajo\ promocion\ humana\).iso

o comillas:

bchunk "Software Libre (Trabajo promocion humana).bin" "Software Libre Trabajo promocion humana).cue" "Software Libre (Trabajo promocion humana).iso"

```

---

### Post by guillermolisi on 2009-08-11
> **euzkoarima said:**
> Parece que no le gusta el paréntesis.
Yo probaría, primero poniendo entre comillas

```
bchunk "Software Libre (Trabajo promocion humana).bin" "Software Libre (Trabajo promocion humana).cue" "Software Libre (Trabajo promocion humana).iso"
```Y si no funciona, idem pero sin los ( ) en el nombre.

Saludos,
Eduardo
Si no le pone algun juego de caracteres que logre un parsing completo del nombre seguira interpretando los ().

Ya mencione que los espacios intermedios en los nombres de archivos no son parte de la mejores practicas y di una alternativa para usar a cambio de eso y de utilizar "\" para que no interprete los espacios.

En los ejemplos mencionados, Software Libre es una etiqueta ? El nombre de un directorio ?

Como es textualmente el nombre del archivo de entrada, del que posee sufijo .bin ?

---

### Post by guillermolisi on 2009-08-11
> **Mister X said:**
> Para los parentesis tambien necesitas el caracter de escape:
```

bchunk Software\ Libre\ \(Trabajo\ promocion\ humana\).bin Software\ Libre\ \(Trabajo\ promocion\ humana\).cue Software\ Libre\ \(Trabajo\ promocion\ humana\).iso

o comillas:

bchunk "Software Libre (Trabajo promocion humana).bin" "Software Libre Trabajo promocion humana).cue" "Software Libre (Trabajo promocion humana).iso"

```
+1 siempre que los nombres de los archivos sean los correctos.

---

### Post by alejandromafer on 2009-08-13
Yo uso el devede para grabar videodvd y tiene una opcion para que lo grabe directamente en .iso, no probaste con eso?

---

### Post by andy_91 on 2009-08-13
> **euzkoarima said:**
> Parece que no le gusta el paréntesis.
Yo probaría, primero poniendo entre comillas

```
bchunk "Software Libre (Trabajo promocion humana).bin" "Software Libre (Trabajo promocion humana).cue" "Software Libre (Trabajo promocion humana).iso"
```

Y si no funciona, idem pero sin los ( ) en el nombre.

Saludos,
Eduardo


alavadas sean las comillas :P

Muchas gracias

> **guillermolisi said:**
> 
En los ejemplos mencionados, Software Libre es una etiqueta ? El nombre de un directorio ?

Como es textualmente el nombre del archivo de entrada, del que posee sufijo .bin ?


el nombre del archivo es Software Libre (Trabajo promocion humana)

> **alejandromafer said:**
> Yo uso el devede para grabar videodvd y tiene una opcion para que lo grabe directamente en .iso, no probaste con eso?

no tengo lectora de dvd solo de cd, el preyecto es un svcd

```
andy@andy-desktop:~$ bchunk "Software Libre (Trabajo promocion humana).bin" "Software Libre (Trabajo promocion humana).cue" "Software Libre (Trabajo promocion humana).iso"
binchunker for Unix, version 1.2.0 by Heikki Hannikainen <hessu@hes.iki.fi>
	Created with the kind help of Bob Marietta <marietrg@SLU.EDU>,
	partly based on his Pascal (Delphi) implementation.
	Support for MODE2/2352 ISO tracks thanks to input from
	Godmar Back <gback@cs.utah.edu>, Colas Nahaboo <Colas@Nahaboo.com>
	and Matthew Green <mrg@eterna.com.au>.
	Released under the GNU GPL, version 2 or later (at your option).

Reading the CUE file:

Track  1: MODE2/2352    01 00:00:00
Track  2: MODE2/2352    00 00:04:00 01 00:06:00
Track  3: MODE2/2352    00 07:33:16 01 07:35:16
Track  4: MODE2/2352    00 15:02:58 01 15:04:58
Track  5: MODE2/2352    00 22:31:18 01 22:33:18
Track  6: MODE2/2352    00 25:05:26 01 25:07:26
Track  7: MODE2/2352    00 27:55:13 01 27:57:13
Track  8: MODE2/2352    00 34:59:65 01 35:01:65
Track  9: MODE2/2352    00 42:59:02 01 43:01:02
Track 10: MODE2/2352    00 51:00:71 01 51:02:71
Track 11: MODE2/2352    00 58:37:14 01 58:39:14

Writing tracks:

 1: Software Libre (Trabajo promocion humana).iso01.iso                            0/0    MB  [********************] 100 %
 2: Software Libre (Trabajo promocion humana).iso02.iso                           65/65   MB  [********************] 100 %
 3: Software Libre (Trabajo promocion humana).iso03.iso                           65/65   MB  [********************] 100 %
 4: Software Libre (Trabajo promocion humana).iso04.iso                           65/65   MB  [********************] 100 %
 5: Software Libre (Trabajo promocion humana).iso05.iso                           22/22   MB  [********************] 100 %
 6: Software Libre (Trabajo promocion humana).iso06.iso                           24/24   MB  [********************] 100 %
 7: Software Libre (Trabajo promocion humana).iso07.iso                           61/61   MB  [********************] 100 %
 8: Software Libre (Trabajo promocion humana).iso08.iso                           69/69   MB  [********************] 100 %
 9: Software Libre (Trabajo promocion humana).iso09.iso                           70/70   MB  [********************] 100 %
10: Software Libre (Trabajo promocion humana).iso10.iso                           66/66   MB  [********************] 100 %
11: Software Libre (Trabajo promocion humana).iso11.iso                           57/57   MB  [********************] 100 %

```

muy bien, pero me ahora tengo mas archivos pequeños

---

### Post by guillermolisi on 2009-08-13
> **andy_91 said:**
> 
el nombre del archivo es Software Libre (Trabajo promocion humana)

Bueno, para el ambito Linux, deberias rebautizarlo a algo asi como 

Software_Libre_(Trabajo_promocion_humana)

y te olvidas de comillas y demas accesorios.

Te vas a ahorrar cantidad de inconvenientes como el que tuviste.

---

### Post by andy_91 on 2009-08-13
> **guillermolisi said:**
> Bueno, para el ambito Linux, deberias rebautizarlo a algo asi como 

Software_Libre_(Trabajo_promocion_humana)

y te olvidas de comillas y demas accesorios.

Te vas a ahorrar cantidad de inconvenientes como el que tuviste.

eso fue lo primero que hice y no me sirvio

---

### Post by pablo.s on 2009-08-13
Más facil:

Renombrá los archivos a
Soft.cue y Soft.bin y procedé.
Cuando tengas la .iso la
renombrás al original 
(Software_Libre, etc..)

---

