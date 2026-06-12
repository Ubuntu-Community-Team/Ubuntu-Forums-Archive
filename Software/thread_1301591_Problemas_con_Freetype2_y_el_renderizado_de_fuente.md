---
title: "Problemas con Freetype2 y el renderizado de fuentes"
date: 2009-10-26
forum: Software
---

### Post by oscarsantis on 2009-10-26
Uso Ubuntu 9.04 en un laptop Sony PCG-K12FP.
Hace unos días compilé e instalé [freetype2]("http://freetype.sourceforge.net/index2.html") ya que me lo pedía Gem, extensión de Puredata, para ser compilada.
Coloqué use el comando ```
./configure --prefix=/usr
```, compilé con **make**y despues lo instalé como superusuario con el comando **sudo make install**. Hasta ahí no hubo problema, salvo que la apariencia o renderizado normal de las fuentes en Ubuntu cambió. Al no quedar conforme con esto procedí a desinstalar la librería con el comando ```
sudo make uninstall
```.
La consola indicó esta información:
```
./builds/unix/libtool --mode=uninstall rm -f /usr/lib/libfreetype.la
libtool: uninstall: rm -f /usr/lib/libfreetype.la /usr/lib/libfreetype.so.6.3.22 /usr/lib/libfreetype.so.6 /usr/lib/libfreetype.so /usr/lib/libfreetype.a
rm -f /usr/include/freetype2/freetype/config/*
rmdir /usr/include/freetype2/freetype/config
rm -f /usr/include/freetype2/freetype/*
rmdir /usr/include/freetype2/freetype
rmdir /usr/include/freetype2
rm -f /usr/include/ft2build.h
rm -f /usr/bin/freetype-config
rm -f /usr/share/aclocal/freetype2.m4
rm -f /usr/lib/pkgconfig/freetype2.pc
```

Despues de ésto traté de abrir otros programas pero el sistema no lo permitía, Desde la consola inteté abrir xterm y me dió este mensaje:

```
xterm: error while loading shared libraries: libfreetype.so.6: cannot open shared object file: No such file or directory
```

Volví a reinstalar la librería y los programas se abren sin problema, sin embargo el problema con la apariencia de las fuentes persiste.
Me imagino que esto radica en este archivo ```
libfreetype.so.6
```.
Me interesa saber cómo puedo recuperar la configuración original de Ubuntu.
Saludos y gracias

---

### Post by moreback on 2009-10-26
Revisa el directorio **/etc/fonts/conf.d**, dentro hay varios archivos que sirven para la configuración de las fuentes, en particular** 10-hinting.conf** y **10-hinting-slight.conf**

Saludos.

---

### Post by oscarsantis on 2009-10-28
Revisé esos archivos y además mandé un correo a los creadores de freetype. A continuaciín te copio la respuesta:

> You need to restore the original version from the Ubuntu package.

That is, you probably want to do something like:

 aptitude reinstall libfreetype6 libfreetype6-dev

as root, to force it to download and reinstall the packaged
version. (Installing the latter package will get you the files you need
to build other programs against Freetype too, which'll probably solve
your original problem.)

Hice lo que me recomendaron, desinstalé la fuente que había compilado y reinstalé vía terminal el paquete que corresponde a la versión oficial de Ubuntu. Sin embargo, el problema persiste.
No se en que lugar la configuración del renderizado cambió y no se restableció en la reinstalación. Te doy un ejemplo: La tipografía Sans aparece un poco más ancha,la monospace más alta. Otra problema sucede con puredata, la tipografía por defecto es la Bitstreamvera Sans Mono y en la interfaz gráfica se ve más alta, un poco rectangular, siendo que es más cuadrada. Todo esto se suma en que algunos sitios web la apariencia de las letras es con una pésima resolución, letras en bold reventadas, etc.
Como dato siempre he tenido las tipografías seteadas en aspecto monocromo.
Saludos

---

### Post by oscarsantis on 2009-10-28
Gracias por el dato de los archivos, pero no se que modificación hay que hacerle a los datos que aparecen ahí

---

### Post by moreback on 2009-10-30
No entiendo tu problema, ¿podrías adjuntar imágenes mostrando las diferencias que dices que tienen las fuentes?

PD: la tipografía por defecto es DejaVu Sans.

---

