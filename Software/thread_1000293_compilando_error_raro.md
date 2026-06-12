---
title: "compilando error raro"
date: 2008-12-02
forum: Software
---

### Post by MeduZa on 2008-12-02
hola, para mi proyecto cree una libreria estatica que usa una libreria el tema es que me tira un error que nunca antes vi y no se que puede ser (pueden ser muchas cosas ajjajaja pero no caigo que es)

este es el error:
```
Making all in lcdspicer
make[3]: Entering directory `/home/meduza/Projects/gtk_lcdspicer/src/lcdspicer'
 cd ../.. && /bin/bash /home/meduza/Projects/gtk_lcdspicer/missing --run automake-1.9 --gnu  src/lcdspicer/Makefile
src/lcdspicer/Makefile.am:13: use `libdatabasecomm_a_LIBADD', not `libdatabasecomm_a_LDADD'
src/lcdspicer/Makefile.am:31: variable `libwidgets_a_LDFLAGS' is defined but no program or
src/lcdspicer/Makefile.am:31: library has `libwidgets_a' as canonic name (possible typo)
src/lcdspicer/Makefile.am:20: variable `libscreens_a_LDFLAGS' is defined but no program or
src/lcdspicer/Makefile.am:20: library has `libscreens_a' as canonic name (possible typo)
src/lcdspicer/Makefile.am:13: variable `libdatabasecomm_a_LDADD' is defined but no program or
src/lcdspicer/Makefile.am:13: library has `libdatabasecomm_a' as canonic name (possible typo)
make[3]: *** [Makefile.in] Error 1
make[3]: Leaving directory `/home/meduza/Projects/gtk_lcdspicer/src/lcdspicer'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/meduza/Projects/gtk_lcdspicer/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/meduza/Projects/gtk_lcdspicer'
make: *** [all] Error 2

```

yo creo que agregue todos los encabezados bien y agregue los -l, lo diferente a todo lo anterior es que la lubreria que yo hice (libdatabasecomm.a) usa una libreria llamada sqlite3 y eso parece que por alguna razon no le gusta!

estoy usando anjuta para crear el proyecto.

---

### Post by MeduZa on 2008-12-03
ya van 2 dias que no echo una linea de codigo por culpa de este error -.- me revienta este tipo de problemas que no son de programacion sino de linkeo y cosas raras de esas -.-

que diferencia hay entre 
```
libdatabase_a_LDADD = \
	$(DBCOMM_LIBS)

```
y

```
libdatabase_a_LIBADD = \
	$(DBCOMM_LIBS)
```
sigo sin entender porque me da error.

eso de Makefile y configure.ac realmente entiendo poco y nada y leerme el manual me esta sacando de mi prioridad que es mi proyecto.
estoy buscando algun software amigable que me ayude a crear las makefile de una manera mas humana, ahora estoy leyendo uno que se llama ant, si alguien sabe de alguno mejor se lo agradeceria muchisimo

ant no me sirve :( quiero archivos makefile no xml (para eso uso C::B)

ahora estoy mirando cmake

---

### Post by Hei Ku on 2008-12-03
Tenes autotools, pero dicen que CMake es mejor. Y por lo que yo vi, es muuucho mas facil de configurar.

---

### Post by MeduZa on 2008-12-04
al final me morfe el manual de automake y derivados y dentro de todo aunque sigo un poco confundido ya hice algunos avances pero necesito una orientacion, una mano amiga que me diga: " no mira esto es asi" :(

mi proyecto tiene esta estructura (los nombres son ficticios):

```

root del proyecto/         ## directorio raiz
   archivos generales de GNU
   archivos .desktop
   documentacion
   src/                    ## directorio fuentes
      programa1       ## ejecutable1 (fuentes y cabezeras)
      programa2       ## ejecutable2 (fuentes y cabezeras)
      archivos de configuracion
      archivos de datos
      glade/               ## directorio de entorno grafico
          archivos.glade
          imagenes
      iplugines/           ## directorio de plugines de entrada
          plugin1.la
          plugin2.la
      librerias estaticas/ ## directorio con librerias estaticas
          libreria1.a
          libreria2.a
          libreriaN.a

```

ese seria el arbol de mi proyecto
Este proyecto tiene unas librerias estaticas que necesito que se distribuyan que sirven para crear plugines
Tambien tiene 2 ejecutables (uno GTK y el otro de consola) que usan las librerias de "librerias estaticas" sin ningun problema usando #include "librerias estaticas/libreriaX" y -llibreriaX en el linker
y por ahora tengo 2 plugines
Los plugines tiene que acceder a las librerias que estan en la carperta "librerias estaticas", pero no se como hacerlo :( la unica forma que lo logro, es haciendo symlinks en la carperta donde estan los plugines, cosa que es muy cancha, pero funciona; me gustaria hacerlo como tiene que ser, desde el archivo Makefile.am o desde donde sea.
Me estoy leyendo le manual de automake y aunque muchas cosas se me aclararon aun no logro linkearlas.

¿Alguno sabe como hacer esto? creo que voy a hacer un nuevo thread

---

### Post by Hei Ku on 2008-12-04
crea otro thread, y postea el Makefile.am de las librerias estaticas.

---

### Post by MeduZa on 2008-12-05
> **Hei Ku said:**
> crea otro thread, y postea el Makefile.am de las librerias estaticas.

podria postiar todos los make Y_Y espero alguien me ayude

Edit: me puse a ver en otros proyectos (pidgin) y estoy encontrando cosas mas que utiles :) ya creo que lo resolvi (era facil pero si no sabes como es imposible :P )

que interesante la variable (ya la habia visto en el manual pero no supe como ponerla) era asi:
AM_CPPFLAGS = \
	-I$(top_builddir)/iplugins

y esto lo encontre en el pidgin:

```
#
# This part allows people to build their own plugins in here.
# Yes, it's a mess.
#
SUFFIXES = .c .so
.c.so:
	$(LIBTOOL) --mode=compile $(CC) -DHAVE_CONFIG_H -I$(top_builddir) $(AM_CPPFLAGS) $(CFLAGS) -c $< -o tmp$@.lo $(PLUGIN_CFLAGS)
	$(LIBTOOL) --mode=link    $(CC) $(CFLAGS) -o libtmp$@.la -rpath $(plugindir) tmp$@.lo $(LIBS) $(LDFLAGS) -module -avoid-version $(PLUGIN_LIBS)
	@rm -f tmp$@.lo tmp$@.o libtmp$@.la
	@cp .libs/libtmp$@.so* $@
	@rm -f .libs/libtmp$@.*
```

me encantaria saber que hace xD aparentemente marca algo (libtool?) para que se use de esa manera en futuras linkeadas
interesante

---

