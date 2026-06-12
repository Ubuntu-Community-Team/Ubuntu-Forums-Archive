---
title: "openoffice 2.4 no abre, no funciona  (Solucionado)"
date: 2008-06-26
forum: Software
---

### Post by pabloatilio on 2008-06-26
Hola amigos, he instalado las últimas actualizaciones recomendadas hace un par de días de Ubuntu en mis equipos (unos son de arquitectura i386 y otros amd64) y me ha dejado de funcionar openoffice (versión 2.4), aparece la ventana de cuando se carga el programa con la barra de progreso funcionando y todo eso, pero cuando termina no abre nada, antes de las actualizaciones andaba todo perfectamente he probado de ejecutarlo por consola y me tira lo siguiente :

pabloatilio@pabloatilio-desktop:~$ ooffice
javaldx: Could not find a Java Runtime Environment! 
pabloatilio@pabloatilio-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f03caca997c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f03caca9a15]
#2 /usr/lib/libX11.so.6 [0x7f03ce973323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f03ce96ad54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f03ca853c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f03c5ee24c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f03c9ce7bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f03c9cfb386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f03c9cfd0d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f03c9cfd483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f03c5ed3957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c628b76d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c628c16a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c628c82b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c6264f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f03d22104ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f03d21a5322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f03d21e21cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f03bf0fb084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f03bf2cfdb4]

Parece algún conflicto con java, la "solución" que encontré en internet aparece desintalando los paquetes :

openoffice.org-gtk
openoffice.org-gnome 

Si bien desintalando esos paquetes, openoffice funciona perfectamente; cambia un poco el aspecto gráfico de la aplicación ya que se parece a una versión más vieja y aparecen unas barras de desplazamiento horribles, una lástima dada la integración gráfica tan lograda que había antes , tal vez solo sea cuestion de esperar que esto se resuelva con alguna actualización.

Nota: las "comillitas" de la solución son porque si bien pude dejar funcional la aplicación, no me gusta como queda, por eso puse el post a ver si alguien tiene algo más interesante que sugerir

Gracias, Saludos.
Pablo

---

### Post by pabloatilio on 2008-07-02
> **pabloatilio said:**
> Hola amigos, he instalado las últimas actualizaciones recomendadas hace un par de días de Ubuntu en mis equipos (unos son de arquitectura i386 y otros amd64) y me ha dejado de funcionar openoffice (versión 2.4), aparece la ventana de cuando se carga el programa con la barra de progreso funcionando y todo eso, pero cuando termina no abre nada, antes de las actualizaciones andaba todo perfectamente he probado de ejecutarlo por consola y me tira lo siguiente :

pabloatilio@pabloatilio-desktop:~$ ooffice
javaldx: Could not find a Java Runtime Environment! 
pabloatilio@pabloatilio-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f03caca997c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f03caca9a15]
#2 /usr/lib/libX11.so.6 [0x7f03ce973323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f03ce96ad54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f03ca853c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f03c5ee24c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f03c9ce7bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f03c9cfb386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f03c9cfd0d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f03c9cfd483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f03c5ed3957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c628b76d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c628c16a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c628c82b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f03c6264f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f03d22104ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f03d21a5322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f03d21e21cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f03bf0fb084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f03bf2cfdb4]

Parece algún conflicto con java, la "solución" que encontré en internet aparece desintalando los paquetes :

openoffice.org-gtk
openoffice.org-gnome 

Si bien desintalando esos paquetes, openoffice funciona perfectamente; cambia un poco el aspecto gráfico de la aplicación ya que se parece a una versión más vieja y aparecen unas barras de desplazamiento horribles, una lástima dada la integración gráfica tan lograda que había antes , tal vez solo sea cuestion de esperar que esto se resuelva con alguna actualización.

Nota: las "comillitas" de la solución son porque si bien pude dejar funcional la aplicación, no me gusta como queda, por eso puse el post a ver si alguien tiene algo más interesante que sugerir

Gracias, Saludos.
Pablo


Último momento : Hoy salió la actualización que resuelve éste problema, se vuelven a instalar los paquetes openoffice.org-gtk y openoffice.org-gnome y se recupera el aspecto gráfico normal.

---

