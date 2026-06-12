---
title: "Programa para ver la TV"
date: 2008-06-02
forum: Software
---

### Post by anarko on 2008-06-02
Hola, gente ubuntera, cabie mi no tan vieja ATi x800GTO por una ati HD3650, y me percate que con el driver radeon ya no funciona la nueva hd3650, y el driver radeonHD esta verde verde verde, asi que no tube mas opcion que tirarme a los fglrx, el problema es que el fglrx no tiene no se que tipo de overlay YVY ( o como se llame ) y mi faviroto, el tvtime, ya no funciona, asi que estoy buscando alternativas, por ahi uds. me puedan ayudar. 

Nota: kdeTv no es una opcion anda muy mal y no puedo usarlo en fullscreen, zapping lo deje de usar en debian woody de lo mal que andaba y perdio todo mi respeto.

Nota 2: por si alquien se pregunta porque cambie la placa de viedo si la x800gto sobra para compiz fusion mas todo lo que pueda linux hacer es porque soy adicto a los jueguitos ( los cuales tengo originales no asi el sistema operativo en el que corren ). 

Nota 3: por si a alguien le interesa la x800gto esta en venta es pci-e y en hardy anda 10 puntos.

Saludos.

---

### Post by Applelnx on 2008-06-03
Lamentablemente nunca pude correr el tvtime con los controladores de ati. Tenia que deshabilitarlos para que me reconozca la placa de tv. No te puedo ayudar :confused:

---

### Post by faktorqm on 2008-06-03
hay uno que se llama xawtv, y otro que se llama xdtv.

aca explican un poco [http://lubrin.org/dani/ch10s06.html](http://lubrin.org/dani/ch10s06.html)

Espero que te haya servido. Salu2!

---

### Post by anarko on 2008-06-03
gracias por la ayuda, el xawtv no anda bien con los drivers fglrx y ninguno de sus deribados.

---

### Post by anarko on 2008-06-03
Bueno vindo la "gran" convocatoria que tienen mis problemas, dejo una solucion, no es la ideal, pero funciona.
Hay una version de TvTime que tiene soporte para salida con las librerias SDL y con de X11 que no son overlay hay que compilarlo desde el codigo fuente, pero no es nada en que google no ayude.
link : [http://www.mcentral.de/wiki/index.php5/Tvtime](http://www.mcentral.de/wiki/index.php5/Tvtime)

Nota: el rendimiento es muy bajo, en fullscreen( 1400x1050 en mi caso ) se ve claramente que no le da la velocidad, pero por ahi en resoluciones menores y maquinas mas potentes que la mia ande casi bien.Cuadro por cuadro y todo la calidad de video del TvTime es infinitamente superior al programa oficial de la placa de TV en windows Xp.

Sigo a la espera de radonHD.

---

