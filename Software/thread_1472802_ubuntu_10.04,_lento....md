---
title: "ubuntu 10.04, lento..."
date: 2010-05-04
forum: Software
---

### Post by quisano on 2010-05-04
yo instale esta ultima version en mi maquina, un celeron 2.4ghz, 512 de ram, una mx4000 de 64mb, y 80gb de rigido, la cosa es que el s.o me anda lento, tarda en abrir cosas, simplemente al navegar anda como pesado, responde lento, yo lo instale desde un usb al s.o, porque no tenia cd para grabarlo, nose si esto tendra algo que ver, o si simplemente mi pc lo corre bien lo unico que por ser media viejita me permite utilizarlo de esa manera... yo la estaba usando con xp, y me anda bastante rapida la pc, nose... queria saber que es lo que puede causar esta lentitud, bueno desde ya muchas gracias...

---

### Post by jbrosio on 2010-05-04
Hola!
Recién acabo de instalar ubuntu 10.04 Netbook remix, y noto que en mi sistema anda un poco lento. Anteriormente tenía instalado el 9.10 en versión desktop y andaba perfecto.

Tengo una Notebook Acer, intel celeron 550, 2 gb ram.

Muchas Gracias!!!!

---

### Post by guidito73 on 2010-05-04
Estoy usando un Sempron con 1GB de RAM y una Nvidia FX5500 de 256 de RAM y la verdad que anda muy bien. Instalaste algún programa que no haya venido por defecto? Hiciste una instalación limpia o actualizaste desde la anterior?

Danos un poco más de información a ver por dónde puede venir el problema :)

---

### Post by quisano on 2010-05-05
la instalación la hice limpia, desde 0... y programas, desde el principio me anduvo así, fue cambiando y agregando programas y el rendimiento sigue siendo el mismo, se supone que con las características de mi pc tendría que anda bien? o puede que afecte el rendimiento, lo que puedo hacer es intentar instalarlo devuelta pero desde la iso original graba en un cd, talvez cambie en algo no lo se...

---

### Post by alfplayer on 2010-05-05
Qué es lento? Una aplicación? Cuál o Cuáles?

---

### Post by quisano on 2010-05-06
todo en general, tarda un rato en iniciar, un rato en abrir las cosas, y cuando abro el firefox, por ej, y varias ventanas anda re tildado... osea, yo lo veo como que anda medio pesado, como que le cuesta, nose si sera mi pc...

---

### Post by alfplayer on 2010-05-06
Hay distribuciones que funcionan mucho más rápido que Ubuntu.

Se puede intentar hacer todo más rápido deshabilitando el autoinicio para servicios y aplicaciones que no se usan (sería positivo una guía para saber qué servicios y aplicaciones se pueden deshabilitar).

Te recomiendo probar la última versión de Google Chrome, que es mucho más rápido que Firefox.

---

### Post by peioazkarate on 2010-05-30
A mi me ha ocurrido lo mismo en la actualización desde 9.10 a 10.04. No es cuestión de buscar otra distribución más rápida, ni de quitar aplicaciones para acelerar. Se trata de algún tipo de "bug" introducido en la 10.04.

Mira a ver si con "dmesg" te sale algo parecido a esto:
...
[   40.587264] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   40.587382] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   40.587386] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   40.587505] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   45.363600] __ratelimit: 192 callbacks suppressed
...

Yo lo he SOLUCIONADO añadiendo en la linea de comando al kernel de grub lo siguiente:

pci=nomsi pci=nommconf

Espero sirva de ayuda.

---

### Post by guillermolisi on 2010-05-30
> **peioazkarate said:**
> A mi me ha ocurrido lo mismo en la actualización desde 9.10 a 10.04. No es cuestión de buscar otra distribución más rápida, ni de quitar aplicaciones para acelerar. Se trata de algún tipo de "bug" introducido en la 10.04.

Mira a ver si con "dmesg" te sale algo parecido a esto:
...
[   40.587264] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   40.587382] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   40.587386] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   40.587505] do_IRQ: 0.83 No irq handler for vector (irq -1)
[   45.363600] __ratelimit: 192 callbacks suppressed
...

Yo lo he SOLUCIONADO añadiendo en la linea de comando al kernel de grub lo siguiente:

pci=nomsi pci=nommconf

Espero sirva de ayuda.
Tuve ese problema con una mother Asus P5VD2 y lo solucione con ```
pci=nomsi, noaer
``` al poco tiempo de comenzar a usar 9.10.

---

### Post by quisano on 2010-06-30
habia pedido el cd de ubuntu, me lo trajeron, entonces para ver si se solucionaba el problema de la lentitud formatie, y me dispuse a instalarlo desde 0, pero resulta que empieza a instalar lo mas bien, hasta que en un momento se tilda, osea puedo mover el cursor o la ventana... pero no pasa nada, esta asi tiempo y tiempo y no pasa nada... y nose que pueda ser... sera el cd? o mi lectora? o que... la anterior vez lo instale desde un usb, pero me andaba lento... sera eso lo que causaba la lentitud? (el hecho de haberlo instalado desde un usb?)... vere que pasa... gracias de todos modos...

---

