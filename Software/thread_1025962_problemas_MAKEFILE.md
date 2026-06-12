---
title: "problemas MAKEFILE"
date: 2008-12-30
forum: Software
---

### Post by MeduZa on 2008-12-30
por un tiempo ya deje de programar mi proyecto porque no avanzo con el tema del make file, realmente me estoy rindiendo poco a poco, ya prácticamente destruí mi proyecto probando cosas y no funciona ni para tras, trato trato pero no puedo y realmente no consigo nadie que me ayude ni acá ni en internet gral.
mi problema es este:

este es el raíz de mi proyecto:

```
/
+--gtk_lcdspicer/
   +--gui/
+--shared/
+--plugins
```

en gtk_lcdspicer tengo 2 ejecutables:
```
gtk_lcdspicer
   gtk_lcdspicer.cpp
   gtk_lcdspicer.hpp
   gui.cpp
   gui.hpp
lcdspicer
  datos.cpp
  datos.hpp
  lcd.cpp
  lcd.hpp  [depende de libsocks.a]
  lcdspicer.cpp
  lcdspicer.hpp
  lcd_writer.cpp
  lcd_writer.hpp [depende de libwidgets.a libscreens.a libdatabase.a]
  plugin.cpp
  plugin.hpp

```
en gui están los glade y las imágenes eso esta ok

en shared tengo librerías que creo para que en futuro si alguien (o yo) quiero crear plugines ya las tengo echas
por otro lado tengo en otra carpeta

```
shared/
  libsocks.a
    socks.cpp
    socks.hpp
  libdatabase.a  [depende sqlite3 (lib externa)]
    database.cpp
    database.hpp
  libwidgets.a  [depende de libdatabase.a]
    widgets.cpp
    widgets.hpp
  libscreens.a  [depende de libdatabase.a]
    screens.cpp
    screens.hpp
  libarchivos.a
    archivo.cpp
    archivo.hpp
```

y por ultimo la carpeta plugins que por ahora tiene 2 (un echo) plugines

```
plugins/
  system.la [depende de libarchivo]
    system.cpp
    system.hpp
```

mi problema son las dependencias, no se como resolverlas, cuando las resuelvo todo anda mal, armo los makefile pero algo me falta no se como hacerlos, alguien que me pueda ayuda por favor estoy trabado hace un mes en eso

muchas gracias comunidad, espero me ayuden, estoy desesperado, quiero seguir avanzando y esto me a echo hasta agarrarle odio al proyecto :(

---

### Post by Hei Ku on 2008-12-30
Que IDE estas usando? Probaste con el automake del KDevelop?

---

### Post by MeduZa on 2008-12-30
> **Hei Ku said:**
> Que IDE estas usando? Probaste con el automake del KDevelop?

anjuta, no, no proble el de kde, proble code::blocks pero no es lo que busco :(


el anjuta me hace lio por ejemplo cuando tengo una libreria que usa otra libreria entonces empiezan los problemas, los soluciono pero poco a poco me fui trabando

ahi lo estoy instalando :P

---

### Post by Hei Ku on 2008-12-30
También podés postear el Makefile.am que te está dando problemas.
Qué usas para generarlos, autotools o cmake?

---

### Post by MeduZa on 2008-12-30
> **Hei Ku said:**
> También podés postear el Makefile.am que te está dando problemas.
Qué usas para generarlos, autotools o cmake?

autotools y creo que son todos porque con el kdevelop veo cosas que con el otro no creo que mi problema era un error de sintaxis en una variable de makefile
voy a probar y si no posteo todos los makefile (son 4 creo)

---

### Post by MeduZa on 2008-12-30
bueno quedaron asi los make file pero ahi algo que no me cierra (ya compila)

configure.ac
```
dnl Process this file with autoconf to produce a configure script.
dnl Created by Anjuta application wizard.

AC_INIT(gtk_lcdspicer, 0.1, http://lcdspicer.sourceforge.net/)

AM_INIT_AUTOMAKE(AC_PACKAGE_NAME, AC_PACKAGE_VERSION)
AC_CONFIG_HEADERS([config.h])
AM_MAINTAINER_MODE

AC_ISC_POSIX
AC_PROG_CXX
AM_PROG_CC_STDC
AC_HEADER_STDC

dnl ***************************************************************************
dnl Internatinalization
dnl ***************************************************************************
GETTEXT_PACKAGE=gtk_lcdspicer
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE", [GETTEXT package name])
AM_GLIB_GNU_GETTEXT
IT_PROG_INTLTOOL([0.35.0])



AM_PROG_LIBTOOL


PKG_CHECK_MODULES(GTK_LCDSPICER, [gtkmm-2.4 >= 2.8 libglademm-2.4 >= 2.6    ], , [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([

You must have the gtkmm 2.4 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.
])])

PKG_CHECK_MODULES(PLUGIN_SYSTEM, [libstatgrab >= 0.16 libgtop-2.0 >= 2.24 glib-2.0 >= 2.18], , [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([

You must have the libstatgrab 0.16, libgtop 2.0 and glib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.
])])

PKG_CHECK_MODULES(DBCOMM, [sqlite3 >= 3.5.9], , [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([

You must have the sqlite3 3.5.9 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.
])])




AC_OUTPUT([
Makefile
shared/Makefile
po/Makefile.in
plugins/Makefile
gtk_lcdspicer/Makefile
])
```

makefile raiz:
```
## Process this file with automake to produce Makefile.in
## Created by Anjuta

SUBDIRS = po \
	shared \
	gtk_lcdspicer \
	plugins

gtk_lcdspicerdocdir = ${prefix}/doc/gtk_lcdspicer
gtk_lcdspicerdoc_DATA = \
	README\
	COPYING\
	AUTHORS\
	ChangeLog\
	INSTALL\
	NEWS
configdir = $(sysconfdir)
desktopdir = $(datadir)/applications

#Configuration fike
config_DATA = gtk_lcdspicer.conf

#Menu item
desktop_DATA = gtk_lcdspicer.desktop

EXTRA_DIST = \
	$(gtk_lcdspicerdoc_DATA) \
	$(config_DATA) \
	$(desktop_DATA)

INCLUDES = -I$(top_srcdir)/libs -I$(top_srcdir)/plugins \
	-I$(top_srcdir)/gtk_lcdspicer

# Copy all the spec files. Of cource, only one is actually used.
dist-hook:
	for specfile in *.spec; do \
		if test -f $$specfile; then \
			cp -p $$specfile $(distdir); \
		fi \
	done

```

makefile gtk_lcdspicer
```
## Process this file with automake to produce Makefile.in

## Created by Anjuta

INCLUDES = \
	-I$(top_srcdir)/gtk_lcdspicer \
	-I$(top_srcdir)/shared

#AM
gtk_lcdspicer_CPPFLAGS = \
	-DPACKAGE_LOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\" \
	-DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\" \
	$(GTK_LCDSPICER_CFLAGS)

lcdspicer_CPPFLAGS = \
	-DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\" 


AM_CFLAGS =\
	 -Wall\
	 -g

bin_PROGRAMS = \
	gtk_lcdspicer \
	lcdspicer

lcdspicer_SOURCES = \
	datos.cpp  \
	datos.hpp  \
	lcd.cpp  \
	lcd.hpp  \
	lcd_writer.cpp  \
	lcd_writer.hpp  \
	plugin.cpp  \
	plugin.hpp  \
	lcdspicer.cpp  \
	lcdspicer.hpp

lcdspicer_LDADD = \
	$(top_builddir)/shared/libsocks.a \
	$(top_builddir)/shared/libscreens.a \
	$(top_builddir)/shared/libwidgets.a \
	$(top_builddir)/shared/libdatabase.a \
	-ldl \
	-lsqlite3

gtk_lcdspicer_SOURCES = \
	gtk_lcdspicer.cpp\
	gtk_lcdspicer.hpp \
	gui.cpp \
	gui.hpp

gtk_lcdspicer_LDADD = \
	$(GTK_LCDSPICER_LIBS)

SUBDIRS = \
	glade

```

makefile gtk_lcdspicer/glade
```
## File created by the gnome-build tools

gladedir = $(datadir)/gtk_lcdspicer/glade
imagesdir = $(datadir)/gtk_lcdspicer/glade

glade_DATA = gtk_lcdspicer.glade

images_DATA = \
	lcdspicericon120.png\
	LCDSpicerLogo.png

EXTRA_DIST = \
	$(images_DATA) \
	$(glade_DATA)


##  = $(datadir)/pixmaps/pidgin/buttons
```

makefile shared
```

lib_LIBRARIES = \
	libdatabase.a \
	libwidgets.a \
	libscreens.a \
	libarchivos.a \
	libsocks.a 
	

libdatabase_a_SOURCES = \
	database.cpp   \
	database.hpp

libdatabase_a_LIBADD = \
	$(DBCOMM_CFLAGS)

libsocks_a_SOURCES = \
	socks.cpp   \
	socks.hpp

libarchivos_a_SOURCES = \
	archivo.cpp \
	archivo.hpp

libscreens_a_SOURCES = \
	screens.cpp \
	screens.hpp

libscreens_a_LIBADD = \
	$(top_builddir)/shared/libdatabase.a

libwidgets_a_SOURCES = \
	widget.cpp \
	widget.hpp

libwidgets_a_LIBADD = \
	$(top_builddir)/shared/libdatabase.a

## File created by the gnome-build tools

```

makefile plugin
```
## File created by the gnome-build tools

INCLUDES = -I$(top_srcdir)/shared

pluginsdir = \
	$(datadir)/gtk_lcdspicer/plugins

plugins_LTLIBRARIES = \
	system.la

system_la_SOURCES = \
	system.cpp    \
	system.hpp

system_la_LIBADD = \
	$(top_builddir)/shared/libarchivos.a \
	$(PLUGIN_SYSTEM_LIBS)

system_la_LDFLAGS = \
	-module \
	-avoid-version

AM_CPPFLAGS = \
	$(PLUGIN_SYSTEM_CFLAGS)
```

[COLOR="Red"]**lo que no me cierra**[/COLOR] es porque si libdatabase.a compila bien, despues en lcdspicer me pide que ponga libdatabase.a y -lsqlite3, si no los pongo falla, pero libdatabase.a que es el que los usa compila 100%, no entiendo eso.

Bueno si ven algo que este mal me dicen voy a reparar unos errores de codigo (que se generaron por el toqueteo que le di :( )

---

### Post by MeduZa on 2008-12-31
encontre un error :)

puse $(DBCOMM_CFLAGS) en vez de $(DBCOMM_LIBS) eso me resuelve la llamada a DBCOMM desde el programa, cosa que no debia suceder.


pero ahora en libdatabase_a_LIBADD = $(DBCOMM_LIBS) me dice que no encuentra -lsqlite3 (el contenido de la variable) me esta faltando el patch :S pero no entiendo porque si lo pongo en el programa lo encuentra y aca no :(
en el programa la tengo que llamar con LDADD en vez de LIBADD sino me da error

---

### Post by Hei Ku on 2009-01-01
Exactamente qué comando tiras y qué error te tira?

---

### Post by MeduZa on 2009-01-04
el comando era build y el error era que el tipo de dato era incompleto (como cuando declaras algo y no lo definis)
lo solucione al fina pero ahi algo que no me cierra.

las librerias widgets y screens usan la libreria databse que usa sqlite3.
No entiendo porque si database es la que usa sqlite3 me lo pide cuando compilo el programa principal, se supone que me lo tendria que pedir cuando compila database....

si alguien entiende porque pasa eso y tiene una solucion seria muy bueno gracias.

pego los makefiles como quedaron:

---

### Post by MeduZa on 2009-01-04
Raiz:
```
## Process this file with automake to produce Makefile.in
## Created by Anjuta

SUBDIRS = po \
	shared \
	gtk_lcdspicer \
	plugins

gtk_lcdspicerdocdir = ${prefix}/doc/gtk_lcdspicer
gtk_lcdspicerdoc_DATA = \
	README\
	COPYING\
	AUTHORS\
	ChangeLog\
	INSTALL\
	NEWS
configdir = $(sysconfdir)
desktopdir = $(datadir)/applications

#Configuration fike
config_DATA = gtk_lcdspicer.conf

#Menu item
desktop_DATA = gtk_lcdspicer.desktop

EXTRA_DIST = \
	$(gtk_lcdspicerdoc_DATA) \
	$(config_DATA) \
	$(desktop_DATA)

INCLUDES = -I$(top_srcdir)/libs -I$(top_srcdir)/plugins \
	-I$(top_srcdir)/gtk_lcdspicer

# Copy all the spec files. Of cource, only one is actually used.
dist-hook:
	for specfile in *.spec; do \
		if test -f $$specfile; then \
			cp -p $$specfile $(distdir); \
		fi \
	done

```

carperta programas:
```
## Process this file with automake to produce Makefile.in

## Created by Anjuta

INCLUDES = \
	-I$(top_srcdir)/gtk_lcdspicer \
	-I$(top_srcdir)/shared

#AM
gtk_lcdspicer_CPPFLAGS = \
	-DPACKAGE_LOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\" \
	-DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\" \
	$(GTK_LCDSPICER_CFLAGS)

lcdspicer_CPPFLAGS = \
	-DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\" \
	$(DBCOMM_CFLAGS)


AM_CFLAGS =\
	 -Wall\
	 -g

bin_PROGRAMS = \
	gtk_lcdspicer \
	lcdspicer

lcdspicer_SOURCES = \
	datos.cpp  \
	datos.hpp  \
	lcd.cpp  \
	lcd.hpp  \
	lcd_writer.cpp  \
	lcd_writer.hpp  \
	plugin.cpp  \
	plugin.hpp  \
	lcdspicer.cpp  \
	lcdspicer.hpp

lcdspicer_LDADD = \
	$(top_builddir)/shared/libsocks.a \
	$(top_builddir)/shared/libscreens.a \
	$(top_builddir)/shared/libwidgets.a \
	$(top_builddir)/shared/libdatabase.a \
	-ldl \
	$(DBCOMM_LIBS)

gtk_lcdspicer_SOURCES = \
	gtk_lcdspicer.cpp\
	gtk_lcdspicer.hpp \
	gui.cpp \
	gui.hpp

gtk_lcdspicer_LDADD = \
	$(GTK_LCDSPICER_LIBS)

SUBDIRS = \
	glade

```

carperta shared (librerias):
```

lib_LIBRARIES = \
	libdatabase.a \
	libwidgets.a \
	libscreens.a \
	libarchivos.a \
	libsocks.a 
	

libdatabase_a_SOURCES = \
	database.cpp   \
	database.hpp

libdatabase_a_DEPENDENCIES = \
	$(DBCOMM_LIBS)

libdatabase_a_CPPFLAGS = \
	$(DBCOMM_CFLAGS)


	

libsocks_a_SOURCES = \
	socks.cpp   \
	socks.hpp

libarchivos_a_SOURCES = \
	archivo.cpp \
	archivo.hpp

libscreens_a_SOURCES = \
	screens.cpp \
	screens.hpp

libscreens_a_LIBADD = \
	$(top_builddir)/shared/libdatabase.a

libwidgets_a_SOURCES = \
	widget.cpp \
	widget.hpp

libwidgets_a_LIBADD = \
	$(top_builddir)/shared/libdatabase.a

shared_HEADERS = \
	archivo.hpp\
	database.hpp \
	screens.hpp \
	socks.hpp \
	widget.hpp

shareddir = \
	$(pkgincludedir)

EXTRA_DIST = \
	$(shared_HEADERS)

## File created by the gnome-build tools

```

carpeta plugines:
```
## File created by the gnome-build tools

INCLUDES = -I$(top_srcdir)/shared

pluginsdir = \
	$(datadir)/gtk_lcdspicer/plugins

plugins_LTLIBRARIES = \
	system.la

system_la_SOURCES = \
	system.cpp    \
	system.hpp

system_la_LIBADD = \
	$(top_builddir)/shared/libarchivos.a \
	$(PLUGIN_SYSTEM_LIBS)

system_la_LDFLAGS = \
	-module \
	-avoid-version

AM_CPPFLAGS = \
	$(PLUGIN_SYSTEM_CFLAGS)


```

---

### Post by Hei Ku on 2009-01-04
A mi me dejó medio perdido. El formato es bastante diferente de lo que estoy acostumbrado. En parte debe ser porque yo desarrollo para un proyecto de mucho tiempo, que tiene todo el stack de compilación ya muy customizado y usan algunos scripts propios, por el tamaño que tiene.

---

### Post by MeduZa on 2009-01-05
> **Hei Ku said:**
> A mi me dejó medio perdido. El formato es bastante diferente de lo que estoy acostumbrado. En parte debe ser porque yo desarrollo para un proyecto de mucho tiempo, que tiene todo el stack de compilación ya muy customizado y usan algunos scripts propios, por el tamaño que tiene.

por ahora anda todo pero ni idea porque tengo que hacer eso, supongamos que un cliente mio necesita un cafe, yo le tengo que preparar le cafe con una taza, agua, cafe y azucar y al cliente no le interesa eso solo el cafe ! eso es lo que no me cierra mi programa, no necesita linkiar libdatabase ni sqlite3 pero si no los pongo me dice que no sabe que son las funciones que ellos tienen :P

---

