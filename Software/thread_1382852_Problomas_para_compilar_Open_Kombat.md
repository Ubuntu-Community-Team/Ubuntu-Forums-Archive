---
title: "Problomas para compilar Open Kombat"
date: 2010-01-16
forum: Software
---

### Post by atari130xe on 2010-01-16
Gente, como va? resulta que estoy intentando compilar Open Kombat una paradia de Mortal kombat un poco viejita, lo había logrado con ubuntu 8.04 pero ahora en karmic desde el codigo fuente no logro hacerlo. les paso algunos datos a ver si alguien que sepa compilar me tira alguna idea:


Instrucciones del autor:
> LINUX/BSD/MAC OS USERS

So, here's this configure script, right? Yes. Depending on which
version you downloaded it installs the "base" system with all the
characters, or just some characters.

If you got the master package, you can choose to disable some of
the characters with parameters to configure:

  --enable-main           Include main data and binary [default: yes]
  --enable-characters     Include the first batch of characters [default: yes]
  --enable-additional     Include the second batch of characters [default: yes]
  --enable-thirdparty     Include the 3rd party characters [default: yes]

This is intended to help packagers break the master package into smaller
chunks.

To get the entire list of (mostly useless) configure options, call

   ./configure -help

After configure does it's magic, you go

   make
   make install
   openmortal

What to do in case something goes wrong during installation:

   1. Curse me.
   2. Make sure that perl-devel, SDL-devel, SDL_image-devel, SDL_mixer-devel and
      freetype2-devel
   3. Check OpenMortal Bugs tracker on the website.
   4. File new bug report if no solution is found.


Mi ultimo intento:

```
terminal@terminal-desktop:~/Desktop/openmortal-0.7$ :/configure
bash: :/configure: No existe el fichero ó directorio
jose@jose-desktop:~/Desktop/openmortal-0.7$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for working const... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for IMG_Load in -lSDL_image... no
[COLOR="Red"]configure: error: *** SDL_image library not found![/COLOR]
terminal@terminal-desktop:~/Desktop/openmortal-0.7$ 

```

La linea en color rojo es extraña porque si entro a synaptic TENGO ese archivo instalado: libsdl-image1.2 version instalada. 1.2.7-1 

gracias!

PD: este es un juego muy entretenido, realmente no comprendo porque no lo incluyen en los repositorios, aunque imagino que como el proyecto está detenido desde el 2007 si no me equivoco debe ser una razón importante para no hacerlo.

---

### Post by guillermolisi on 2010-01-16
> **atari130xe said:**
> 
```

[COLOR=Red]configure: error: *** SDL_image library not found![/COLOR]
terminal@terminal-desktop:~/Desktop/openmortal-0.7$ 

```La linea en color rojo es extraña porque si entro a synaptic TENGO ese archivo instalado: libsdl-image1.2 version instalada. 1.2.7-1 

gracias!

PD: este es un juego muy entretenido, realmente no comprendo porque no lo incluyen en los repositorios, aunque imagino que como el proyecto está detenido desde el 2007 si no me equivoco debe ser una razón importante para no hacerlo.
Debe estar buscando esa libreria en el lugar equivocado, por eso la tenes pero no la encuentra. Deberia haber un archivo con toda la configuracion para la etapa del "configure" que usa cuando compilas.

---

### Post by Mauro22 on 2010-01-16
Aca tenes algunos debs, a ver si es lo mismo:

[0] [http://www.filewatcher.com/m/openmortal-extra_0.7-1duo%2Betch1_all.deb.36330056.0.0.html](http://www.filewatcher.com/m/openmortal-extra_0.7-1duo%2Betch1_all.deb.36330056.0.0.html)

---

### Post by atari130xe on 2010-01-18
Gracias por las respuestas! encontré las librerias que me faltaban, hasta lo empaqueté en un .deb yo mismo asi que si quieren lo trato de subir a algun sitio y lo bajan de ahi, probé en 2 maquinas más y en una funciono de una y en la otra tiene un problema para arrancar.
gracias!

---

