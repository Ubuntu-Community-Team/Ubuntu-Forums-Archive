---
title: "Network Manager"
date: 2008-09-04
forum: Software
---

### Post by Vero1 on 2008-09-04
Hola a todos,

Desde hace un tiempo que me salen unas advertencias sobre el Network Manager.

Hoy, al querer correr NM desde Terminal, me sale lo siguiente:

(network-admin:7948): Gtk-WARNING **: Unknown property: GtkComboBox.items

Alguien me puede decir qué significa y qué tengo que hacer?

Por otra parte si pongo en Terminal nm-applet no me sale nada.

Gracias de antemano y saludos

p.d. donde sale la carita va un 8 o sea el número es 7948.

---

### Post by WanderingKnight on 2008-09-04
Se me ocurre que el codigo se esta refiriendo a una funcion que no puede encontrar en las bibliotecas de GTK que vos tenes... tal vez te convendria chequear la version de las bibliotecas de las que depende network-manager-gnome que tenes instaladas?

> bilkis@bilkis-kubuntu:~/downloads$ apt-cache show network-manager-gnome
Package: network-manager-gnome
Priority: optional
Section: net
Installed-Size: 1908
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: network-manager-applet
Version: 0.6.6-0ubuntu3
Depends: gksu, libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0), libgnome-keyring0 (>= 2.22.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libnm-util0, liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.20.1), libpixman-1-0, libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.10), libsm6, libx11-6, libxml2, libxrender1, network-manager (>= 0.6.5), zlib1g (>= 1:1.2.3.3.dfsg-1)

La verdad que otra cosa no se me ocurre, y es raro que haya empezado a pasar de golpe.

Igual si es solo un warning y el coso sigue corriendo igual no creo que haya nada de lo que preocuparse...

---

### Post by Vero1 on 2008-09-05
Hola, gracias por responder.

Tengo todas las librerías que me mostrás, salvo que mi network-manager es 
0.6.6, no sé si influye en algo.

Ahora, si voy a Terminal y pongo network-manager no pasa nada y si pongo nm-applet tampoco. Es ésto normal?

saludos

---

### Post by cdesseno on 2008-09-05
Y si probás remplazándolo por el Wicd?

---

### Post by Vero1 on 2008-09-05
Hola, gracias por responder.

Me contesta orden no encontrada...

saludos

---

