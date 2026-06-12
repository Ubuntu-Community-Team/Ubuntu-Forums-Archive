---
title: "error kazehakase"
date: 2008-12-23
forum: Software
---

### Post by andy_91 on 2008-12-23
una consultita: cuando voy al menu edit-preference... en el kazehakase se me cierra

en el terminal me sale esto

> $ kazehakase

(kazehakase:5770): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(kazehakase:5770): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gtype.c:3362: type id `0' is invalid

(kazehakase:5770): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Fallo de segmentación


desde ya muchas gracias...

---

### Post by Jakeukalane on 2010-04-07
Hola: 

A mí me pasaba pero porqué se me conjeló.

Al intentar recuperar la sesión anterior aparecía un error similar. Para solucionarlo borre los archivos que tenían current-session de la carpeta /home/USUARIO/.kazehakase y todo funcionó normal.

La sugerencia que te doy es que hagas un back-up con las preferencias, las borres y luego intentes modificar las preferencias en kazehakase. Parece que no estan en esa misma carpeta.....

Si las habías editado antes lo más probable es que con reinstalar se solucione todo. Si es una versión recién instalada no sé que puede pasar la verdad.


Suerte y saludos

---

