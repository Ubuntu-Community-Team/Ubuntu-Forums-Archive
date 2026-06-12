---
title: "DVD no quiere colaborar"
date: 2009-11-17
forum: Software
---

### Post by Mauro22 on 2009-11-17
Seguro que alguno sabe qué es esto:

[IMG]http://img26.imageshack.us/img26/7808/pantallazoig.png[/IMG]



Ven el Cuadradito en el nombre del DVD... Ahora sólo pasa en Ubuntu Karmic, como pueden apreciar.


Este es un problema que vengo arrastrando desde JJ.. pero nunca le di mucha bola, ya que no uso la PC para ver dvd's... pero me dieron ganas de ripearlo para no andar con el dvd de un lado al otro.


Busqué en el foro y mucho no encontré... Google pero no tengo idea de como buscarlo...

Puede ser algo de las tipografias?? Aunque del "otro" lado no haya  nada??

[B]Resumen:

Ubuntu JJ, KK, Ventanas [Virtual]: [/B]

Lo monta perfecto. No reproduce (aclama 'No se puede leer'). No deja copiarlo // ripearlo.


**Reproductor estandar de DVD:**

OK



No me decido si va en Soft o en Hard... porqué no se a cual pertenece. Otros DVDs se ven bien y se puede hacer de todo con ellos; es este solo...



Alguna idea?

Gracias!! ;)

---

### Post by pablo.s on 2009-11-17
> **Mauro22 said:**
> Puede ser algo de las tipografias?? Aunque del "otro" lado no haya  nada??

Efectivamente, el titulo está
escrito con un caracter que no está
en la tabla UNICODE y casi casi con
certeza te diria que ese es el problema.
Una solución rápida es copiar los 
contenidos del DVD a otro pero esta vez
con un titulo sin el caracter que "ofende"
a Nautilus. Suele pasar con acentos o
simbolos mal escritos desde <Sistema
propietario de marca registrada>.
Cómo en ese sistema operativo se suelen
utilizar codificaciones no standard, al
transladarlos a sistemas que si lo hacen,
generan este tipo de conflictos.

---

### Post by Mauro22 on 2009-11-17
Y como lo grabo?? 

Ubuntu no puede
xp virtual no puede
vista en otra notebook dice que el DVD no es de zona 4 sino 1... Lo cual es mentira porque el DVD esta hecho acá y dice Zona 4.


Forma de montarlo con otro nombre o hacer que ubuntu no ponga el titulo como nombre??


Gracias Pablo!

---

### Post by pablo.s on 2009-11-17
> **Mauro22 said:**
> Forma de montarlo con otro nombre o hacer que ubuntu no ponga el titulo como nombre??

Si Ubuntu lo puede montar, copiá
la carpeta VIDEO_TS a una carpeta
en el escritorio.
Luego vas al <Sistema propietario de 
marca registrada> y te fijás el nombre
que tiene el disco, pero el último caracter
prestá especial atención de cual se trata.
Volvés a Ubuntu y grabás como DVD de
Video, con el nombre correcto y recreando
la carpeta AUDIO_TS dentro del disco.
Supongo que deberia funcionar.

---

### Post by Mauro22 on 2009-11-17
EDIT!


Solucionado: Al parecer (ando investigando) alguna actualización hizo un lio con el libdvdcss.


Hice esto:

sudo /usr/share/doc/libdvdread4/install-css.sh


reinicié y listo :D



Perdón por las molestias.

---

