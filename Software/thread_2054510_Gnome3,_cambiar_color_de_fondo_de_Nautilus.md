---
title: "Gnome3, cambiar color de fondo de Nautilus"
date: 2012-09-07
forum: Software
---

### Post by EnriqueK on 2012-09-07
Uso Precise ,Gnome3 y escritorio clásico , quisiera poder cambiar el color de fondo de las ventanas de Nautilus, estoy usando el tema Adwaita, el fondo por defecto es blanco y quisiera cambiarlo a negro
Lo que hice hasta ahora y que no dió resultado fué
sudo gedit /usr/share/themes/Adwaita/gtk-3.0/settings.ini
reemplazo #ffffff que es el código hexadicimal del color blanco por #000000 que es del color negro , poeo como dije antes, no funciona

---

### Post by hictio on 2012-09-08
Probaste con algún setting de gconftool-2?
Algo de /apps/nautilus/preferences o similar?
Con gsettings y org.gnome.nautilus.preferences no parece haber nada para eso.

---

### Post by EnriqueK on 2012-09-08
Casi lo logro
1.- Creo una copia del tema Adwaita en /home/usuario/.themes cambio el nombre a 2Adwaita y selecciono este tema usando
gnome-tweak-tool
2.-Entro a la carpeta del tema y edito el archivo /home/usuario/.themes/2Adwaita/gtk-3.0/gtk.css
Mostraba esto
@import url("resource:///org/gnome/adwaita/gtk-main.css");
y lo dejo así
#@import url("resource:///org/gnome/adwaita/gtk-main.css");
background-color: #000000;

Luego reinicio sesión o ejecuto
killall nautilus

No es del todo satisfactorio por que afecta a otras aplicaciones y lo que deseo es que solo sea para Nautilus, pero sin dudas es un avance.
Aclaro que #000000 es el cogido HTML del color negro, si se desea otro color pueden usar por ejemplo Gimp y seleccionan el código HTML del color que quieran

---

### Post by hictio on 2012-09-09
No probaste bajándote algún tema de [Gnome Look - GTK3](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=3a16f1255ba5c0abf271de491b03ebd6) que tenga el setup de colores como te gusta para ver cómo lo hicieron?

---

