---
title: "Error interno en Inkscape 0.48"
date: 2011-03-28
forum: Software
---

### Post by harryscode on 2011-03-28
Hola, mi problema es el siguiente. No puedo imprimir nada con inkscape debido a un error interno. Al correrlo por consola me tira lo siguiente:

(inkscape:6687): gtkmm-WARNING **: gtkmm: Attempt to call Gtk::manage() on a Gtk::Window, but a Gtk::Window has no parent container to manage its lifetime.

inkscape: /build/buildd/cairo-1.9.6/src/cairo-surface.c:365: _cairo_surface_begin_modification: La declaración `! surface->finished' no se cumple.

Emergency save activated!

Emergency save document locations:
  /home/diego/Documento nuevo 1.2011_03_28_21_04_07.0.svg
Emergency save completed. Inkscape will close now.
If you can reproduce this crash, please file a bug at [www.inkscape.org](www.inkscape.org)
with a detailed description of the steps leading to the crash, so we can fix it.
Abortado


A alguien le paso algo parecido?. No recuerdo haber hecho ninguna modificación en el sistema para que justifique el error, hasta hace un par de días funcionaba sin problemas y hoy empezó con eso. 
Si alguien tiene data, más que agradecido.

---

### Post by harryscode on 2011-03-28
Bueno, rápidamente enviaron respuesta.

*** This bug is a duplicate of bug 600622 ***
   [https://bugs.launchpad.net/bugs/600622](https://bugs.launchpad.net/bugs/600622)

> inkscape: /build/buildd/cairo-1.9.6/src/cairo-surface.c:365: (…)

You are using an outdated snapshot version of cairo which causes
inkscape to crash when printing or opening the print preview. It was
fixed in cairo snapshot 1.9.12, and the fix is also in the current
stable version 1.10.

Linking as duplicate to
Bug #600622 in cairo (Ubuntu): “inkscape assert failure: inkscape: /build/buildd/cairo-1.9.10/src/cairo-surface.c:337: _cairo_surface_begin_modification: Assertion `! surface->finished' failed.”
<https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/600622>

Please add a comment here and revert the duplicate status if you don't
agree and think these are different issues.

** Tags added: crash printing

** This bug has been marked a duplicate of bug 600622
  inkscape assert failure: inkscape: /build/buildd/cairo-1.9.10/src/cairo-surface.c:337: _cairo_surface_begin_modification: Assertion `! surface->finished' failed.

Encontré el fix... pero tengo un problema para compilarlo.. asi que abro otro thread.

---

