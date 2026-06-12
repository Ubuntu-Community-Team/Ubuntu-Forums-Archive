---
title: "Al mirar videos de Youtube el monitor se apaga a las 10 minutos"
date: 2012-05-16
forum: Software
---

### Post by autusgo on 2012-05-16
Básicamente lo que pasa es lo que dice el título, por lo que estuve leyendo en otros lados a muchos les pasa lo mismo pero con el protector de pantalla. Ahora bien, ya sé como evitar esto, pero no quiero desabilitar la opción de apagado de patalla, simplemente **quiero que el sistema se de cuenta que la estoy usando y no apague la pantalla**, tal como lo hace Windows (algo que Windows hace bien).

Me bajé algo llamado Caffeine que se supone que se encarga de eso; bajó, instaló, me aparece el ícono en el menú, pero le doy click no pasa NADA.

Alguna idea? No hay forma de que el sistema por sí solo se de cuenta de que estoy viendo un video y no me apague la pantalla? Necesito sí o sí la aplicación? Realmente no quiero modificar las opciones de ahorro de energía, porque muchas veces dejo la PC inactiva y me voy a hacer otra cosa.

Uso Kubuntu 11.10

Gracias!

PD. Agrego el error que me tira, va cambiando un poco a medida que pruebo cosas nuevas, pero en escencia es siempre el mismo:

> ERROR:root:Could not find any typelib for AppIndicator3
ERROR:root:Could not find any typelib for Notify
Please install pynotify
ERROR:root:Could not find any typelib for Notify
Traceback (most recent call last):
  File "/usr/bin/caffeine", line 40, in <module>
    import caffeine
  File "/usr/bin/../share/pyshared/caffeine/__init__.py", line 154, in <module>
    from caffeine.main import main
  File "/usr/bin/../share/pyshared/caffeine/main.py", line 47, in <module>
    import core
  File "/usr/bin/../share/pyshared/caffeine/core.py", line 21, in <module>
    from gi.repository import Gtk, GObject, Gio, Notify
ImportError: cannot import name Notify

---

