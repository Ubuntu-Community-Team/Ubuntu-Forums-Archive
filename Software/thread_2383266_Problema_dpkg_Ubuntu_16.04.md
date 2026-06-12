---
title: "Problema dpkg Ubuntu 16.04"
date: 2018-01-22
forum: Software
---

### Post by juanmatiascba on 2018-01-22
Buenas comunidad.

Les cuento el inconveniente que tengo. Acabo de instalar ubuntu 16.04, despues de borrar Xubuntu 16.04. Respalde home, pise el home de Ubuntu. Ademas respalde la lista de programas instalados y paquetes que tenia en xubuntu:

Respectivamente:
dpkg –get-selections > paquetes
Y guarde los paquetes que estaban en /var/cache/apt/archives

El problema surgio cuando instale estos paquetes en Ubuntu; utilizando:

sudo dpkg -i *.deb

Dejo algo del problema de dependencias que surgio:

```

~/Documentos/Paquetes/archives$ sudo dpkg -i *.deb
Seleccionando el paquete breeze-icon-theme previamente no seleccionado.
(Leyendo la base de datos ... 177406 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar breeze-icon-theme_4%3a5.18.0-0ubuntu1_amd64.deb ...
Desempaquetando breeze-icon-theme (4:5.18.0-0ubuntu1) ...
Seleccionando el paquete docbook-xsl previamente no seleccionado.
Preparando para desempaquetar docbook-xsl_1.79.1+dfsg-1_all.deb ...
Desempaquetando docbook-xsl (1.79.1+dfsg-1) ...
Seleccionando el paquete extlinux previamente no seleccionado.
Preparando para desempaquetar extlinux_3%3a6.03+dfsg-11ubuntu1_amd64.deb ...
...

dpkg: error al procesar el paquete qml-module-qtquick-controls:amd64 (--install):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de qml-module-qtquick-dialogs:amd64:
 qml-module-qtquick-dialogs:amd64 depende de libstdc++6 (>= 4.1.1); sin embargo:
 El paquete `libstdc++6:amd64' no está configurado todavía.

dpkg: error al procesar el paquete qml-module-qtquick-dialogs:amd64 (--install):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de qml-module-qtquick-layouts:amd64:
 qml-module-qtquick-layouts:amd64 depende de libstdc++6 (>= 4.1.1); sin embargo:
 El paquete `libstdc++6:amd64' no está configurado todavía.

dpkg: error al procesar el paquete qml-module-qtquick-layouts:amd64 (--install):
 problemas de dependencias - se deja sin configurar
dpkg: demasiados errores, parando
Procesando disparadores para man-db (2.7.5-1) ...
Procesando disparadores para fontconfig (2.11.94-0ubuntu1.1) ...
Procesando disparadores para gnome-menus (3.13.3-6ubuntu3.1) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu5.1) ...
Procesando disparadores para bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para mime-support (3.59ubuntu1) ...
Procesando disparadores para hicolor-icon-theme (0.15-0ubuntu1) ...
Procesando disparadores para dbus (1.10.6-1ubuntu3.3) ...
Procesando disparadores para libc-bin (2.23-0ubuntu9) ...
Procesando disparadores para udev (229-4ubuntu19) ...
Procesando disparadores para install-info (6.1.0.dfsg.1-5) ...
Procesando disparadores para doc-base (0.10.7) ...
Procesando 1 archivo doc-base añadido...
Se encontraron errores al procesar:
 libsystemd0_229-4ubuntu19_i386.deb
 fonts-dejavu
 gcc-5-base:i386
 gcc-5-base:amd64
 kde-runtime
 kdoctools
 libcups2:i386
 libcups2:amd64
 libdbus-1-3:i386
 libgd3:i386
 libgd3:amd64
 libgphoto2-6:i386
 libidn11:i386
 libidn11:amd64
 libkhtml5
 libllvm4.0:i386
 libllvm4.0:amd64
 libopenal1:i386
 libplasma3
 libpulse0:i386
 libpulse0:amd64
 libqtwebkit4:amd64
 libsane:i386
 libsdl-image1.2:amd64
 libstdc++6:i386
 libstdc++6:amd64
 libstreamanalyzer0v5
 libstreams0v5
 libthreadweaver4
 libtxc-dxtn-s2tc0:i386
 libusageenvironment3:amd64
 libva-x11-1:amd64
 libvlccore8
 libvoikko1:amd64
 libxml2:i386
 libxml2:amd64
 libxml2-utils
 libxslt1.1:i386
 okular
 p7zip
 p7zip-full
 phonon-backend-gstreamer:amd64
 plasma-framework
 plasma-scriptengine-javascript
 qml-module-org-kde-activities:amd64
 qml-module-org-kde-kquickcontrols:amd64
 qml-module-org-kde-kquickcontrolsaddons:amd64
 qml-module-qtquick2:amd64
 qml-module-qtquick-controls:amd64
 qml-module-qtquick-dialogs:amd64
 qml-module-qtquick-layouts:amd64
Proceso detenido por haber demasiados errores.

```

La salida completa:
[https://paste.ubuntu.com/26441666/](https://paste.ubuntu.com/26441666/)

Bueno gente, parece que fue muy mala idea instalar paquetes tan masivamente entre diferentes distros. Estoy abierto a posibles soluciones, desacher los paquetes instalados. Para no llegar a medida extrema de volver a instalar ubuntu.

Saludos!

---

### Post by tinylagarto on 2018-01-23
No estoy muy seguro lo que está pasando pero probaría un:

```
sudo apt install -f
```

---

### Post by juanmatiascba on 2018-01-24
> **ivanovnegro2 said:**
> No estoy muy seguro lo que está pasando pero probaría un:

```
sudo apt install -f
```

Parece que eso soluciono los paquetes. Muchas gracias!

---

### Post by tinylagarto on 2018-01-24
A veces es necesario usar este comando para bajar todas las dependencias de los paquetes o para quitar paquetes dañados.

---

