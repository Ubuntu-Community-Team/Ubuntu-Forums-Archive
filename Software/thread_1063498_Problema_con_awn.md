---
title: "Problema con awn"
date: 2009-02-07
forum: Software
---

### Post by feche_mza on 2009-02-07
Bueno resulta que tengo un par de problemas medio raros con awn, el primero y el que mas me molesta es uno con el applet del menu, lo toco una ves para abrir cualquier programa y joya, pero si lo toco de nuevo desaparece el icono, y tengo que apagar awn y volverlo a prender o sacar y volver a poner el applet, lo mas raro es que cuando de borra solo si abro awn manager me aparece como activado, pero en la barra no aparece, probe reinstalandolo, con una vercion anterior, con distintos repositorios pero es lo mismo.
el segundo es con un lanzador de nautilus, nada complicado es un lanzador que me abre nautilus como si pusieras nautilus en terminal, el problema es que no me lo abre, tengo que reiniciar awn para que ande tirenme una mano porfa!!!

ahh me olvidaba cuando lo ejecuto en terminal me tira esto > fedde@fedde-desktop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/main-menu.desktop
APPLET : /usr/share/avant-window-navigator/applets/stacks.desktop
APPLET : /usr/share/avant-window-navigator/applets/stacks.desktop
APPLET : /usr/share/avant-window-navigator/applets/stacks.desktop
APPLET : /usr/share/avant-window-navigator/applets/separator.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-16.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-10.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-12.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-14.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-9.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-6.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-15.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-17.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-8.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-7.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-2.desktop
LOADED : /home/fedde/.config/awn/launchers/awn_launcher-18.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/trasher.desktop
** Message: don't know how to handle audio/AMR, codec_data=(buffer)0000001164616d724d4f544f0081ff0001, rate=(int)8000, channels=(int)1
** Message: don't know how to handle audio/AMR, codec_data=(buffer)0000001164616d724d4f544f0081ff0001, rate=(int)8000, channels=(int)1
** Message: don't know how to handle audio/AMR, codec_data=(buffer)0000001164616d724d4f544f0081ff0001, rate=(int)8000, channels=(int)1
/usr/share/avant-window-navigator/applets/stacks/stacks_gui_curved.py:1224: PangoWarning: Invalid UTF-8 string passed to pango_layout_set_text()
  pango_layout.set_text(potential_text)
Launched application : 9429
error: duplicate affix flag W in line SFX
warning: incompatible stripping characters and condition:
SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
warning: incompatible stripping characters and condition:
SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX
error: duplicate affix flag W in line SFX


---

### Post by kornykyano on 2009-02-08
A mi también me paso lo mismo con esta barra, desde mi lugar lo que te puedo decir es que reinstala nuevamente pero no de **Launchpad**, si no de los repositorios de Ubuntu. No olvides borrar las carpetas de .config y .gconf/apps que hagan referencia a AWN (en caso lo renombras para no perderlo). A partir de ahí ya no tuve problemas, la contra es que no vas a tener los applets solo podrás colocar lanzadores.

O puedes probar Cairo-Dock u otros.

saludos

---

### Post by feche_mza on 2009-02-08
ya probe eso, la movida es no perder los aplets, pero ahora no lo hace mas, misteriosamente lo dejo de hacer cuando deshabilite algunos efectos de compiz, pero igual gracias

---

