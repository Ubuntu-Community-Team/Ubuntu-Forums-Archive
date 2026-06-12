---
title: "Problema con la barra de menús."
date: 2010-10-27
forum: Software
---

### Post by renzodeleo on 2010-10-27
Hola, desde que se me tildo la computadora, tuve un problema: desaparecieron los botones de preferencias y administracion (solo tengo Ayuda y soporte, acerca de GNOME y acerca de Ubuntu) en el menú de Sistema. El botón de aplicaciones no abre ningún menú. Cuando pongo editar menús no se abre nada. No puedo abrir la termnial (intente hacer un lanzador con la terminal pero aparece un error de 'no se puede crear hijo' algo asi).

Necesito ayuda :(

PD: intente agregar la barra menús para ver si aparecían de nuevo, pero nada.

Gracias por su atencion.

---

### Post by sys.adm.og on 2010-10-27
Presiona ALT+F2 y en la ventana escribe 'alacarte' esto te traera un gestor de menus, te adjunte una imagen de guia.
En la seccion de menus seleccionas sistemas, luego ya en la opcion 'Elementos' marcas los elementos que deseas que aparezcan.

Para abrir un terminal ALT+F2 y en la ventana escribe 'gnome-terminal'

Saludos

---

### Post by renzodeleo on 2010-10-27
gracias por la respuesta, pero sigo sin poder hacer nada :(
cuando pongo eso me aparece:

---

### Post by newtonfn on 2010-10-27
Lamento no tener una buena respuesta para tu problematica y solo te daré algunas sugerencias... pero no se si servirán.

Primero, pareciera que algun archivo de configuración se daño. Podríamos probar si es solamente en el usuario que sueles usar o en todos los usuarios. Mi mayor esperanza es que el problema sea solo de tu usuario.

Como no tenes el menu System, yo crearía un usuario nuevo utilizando los comandos de consola.

Para crear un usuario debes escribir en la consola:
sudo adduser <NombreNuevoUsuario>

Te pedirá una clave y otros datos, que deberás proveer y listo.. tendrás un usuario nuevo para loguearte en tu sistema.

Asi que luego cerraría la sesion (o reiniciaria el sistema si se me complica) y me loguearía luego con el nuevo usuario que creé.

Si en este usuario el menu se ve bien, entonces es un problema de configuración en algun archivo del otro usuario.. y podrías ir copiando/comparando/investigando archivo por archivo del home de los dos usuarios para encontrar donde esta el problema.

Suerte.

---

### Post by sys.adm.og on 2010-10-28
> **renzodeleo said:**
> gracias por la respuesta, pero sigo sin poder hacer nada :(
cuando pongo eso me aparece:

Creo que el problema esta en las librerias de python

prueba esto y dime que resultado te da en la terminal

```
osmar@osmarpc28:~$ dpkg --status alacarte
Package: alacarte
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 1356
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: all
Version: 0.13.1-0ubuntu1
Replaces: smeg
Provides: smeg
Depends: python (>= 2.4), python-support (>= 0.90.0), python-gtk2 (>= 2.13.0), python-gmenu (>= 2.27.92), gnome-menus (>= 2.27.92), python-gobject (>= 2.15.1)
Recommends: gnome-panel
Conflicts: smeg (<< 0.8-0ubuntu1)
Description: easy GNOME menu editing tool
 Alacarte is an easy-to-use menu editor for GNOME that can add
 and edit new entries and menus. It works with the freedesktop.org
 menu specification and should work with any desktop environment
 that uses the spec.
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Python-Version: 2.6

```

Donde dice 'Depends' figuran las dependencias fijate que poseas todas.
Y tambien ver si esta en conflicto con alguna libreria

---

### Post by renzodeleo on 2010-10-28
Gracias por las respuestas.
Hice un nuevo usuario y se fue el problema. ¿Elimino el usuario que no anda bien? ¿Cómo lo hago?
-----
Copie y pegue eso en la terminal (no tengo experiencia, soy nuevo) y salio asi:

---

