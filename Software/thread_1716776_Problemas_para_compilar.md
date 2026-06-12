---
title: "Problemas para compilar"
date: 2011-03-28
forum: Software
---

### Post by harryscode on 2011-03-28
Bien, en consecuencia del thread [http://ubuntuforums.org/showthread.php?p=10612853#post10612853]("http://ubuntuforums.org/showthread.php?p=10612853#post10612853"), decidí tratar de arreglar el problema. Lo primero que hice fue intentar instalar el fix (cairo 1.9.12). Me tiraba el error de que la version de pixman era vieja y debia actualizar. Busque la versión recomendada (0.17.5) y oh casualidad, no existe, baje la más nueva 0.21.6 y la inmediata a la recomendada 0.17.6. Me tiraron un error cuando hacia make. Dije, pense, no encaja la versión con la versión de cairo, asi que decidi bajar la versión más actual de cairo. Pero al compilar me tira el siguiente error:

make  all-recursive
make[1]: se ingresa al directorio «/home/diego/cairo-1.0.2»
Making all in pixman
make[2]: se ingresa al directorio «/home/diego/cairo-1.0.2/pixman»
Making all in src
make[3]: se ingresa al directorio «/home/diego/cairo-1.0.2/pixman/src»
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I.     -g -O2 -MT fbpict.lo -MD -MP -MF ".deps/fbpict.Tpo" -c -o fbpict.lo fbpict.c; \
	then mv -f ".deps/fbpict.Tpo" ".deps/fbpict.Plo"; else rm -f ".deps/fbpict.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I. -g -O2 -MT fbpict.lo -MD -MP -MF .deps/fbpict.Tpo -c fbpict.c  -fPIC -DPIC -o .libs/fbpict.o
/tmp/ccnLmmJW.s: Assembler messages:
/tmp/ccnLmmJW.s:8789: Error: symbol `_cairo_pixman_composite' is already defined
make[3]: *** [fbpict.lo] Error 1
make[3]: se sale del directorio «/home/diego/cairo-1.0.2/pixman/src»
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio «/home/diego/cairo-1.0.2/pixman»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/diego/cairo-1.0.2»
make: *** [all] Error 2
 
con lo cual, no puedo seguir actualizando, y sigo con el problema de no poder imprimir con Inkscape. La pregunta es.. y viendo que desde synaptic no puedo actualizar cairo... es problema de la compilación, o es que en 10.4 no puedo actualizar, sino que debo actualizar todo el sistema a 10.10?.
Disculpas si lo que planteo es una burrada, pero no entiendo mucho y voy más por prueba y error que por otra cosa. Si me pueden ayudar, más que agradecido.

---

### Post by alfplayer on 2011-03-29
El directorio es /home/diego/cairo-1.0.2, y la versión 1.0.2 tiene más de dos años. Por qué  intentas con una versión tan vieja? La versiones 1.9 y 1.10 son mucho más actuales.

---

### Post by harryscode on 2011-03-29
Como ven.. lo mio era una novatada, eso lo hice a las 2 de la mañana y ya no razonaba bien.. y baje una version del 2008. Ni me habia dado cuenta. Ahora estoy bajando la de diciembre de 2010. Veremos si puedo llegar a buen puerto. Gracias por hacerme ver el error alfplayer.

---

### Post by harryscode on 2011-03-31
Solucionado. Actualice Cairo después de actualizar pixman, con las versiones correctas y el problema fue resuelto. Gracias.

---

