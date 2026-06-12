---
title: "Problema con Gwibber"
date: 2010-05-27
forum: Software
---

### Post by Criminel on 2010-05-27
Hola,
Luego de haber funcionado bien un par de días ahora ya no arranca Gwibber.
Probé instalarlo y desinstalarlo tres veces sin resultados.
¿Alguien sabe a qué puede deberse?

---

### Post by FB91 on 2010-05-27
probaste eliminarlo POR COMPLETO y después instalarlo de nuevo?
para eliminarlo completamente usa esto:

```
sudo aptitude remove --purge gwibber
```

y después instalalo de nuevo a ver que pasa

```
sudo aptitude install gwibber
```

---

### Post by Criminel on 2010-05-28
Sí, ya lo había probado, sin resultados.

Gracias igual.

---

### Post by carmepla on 2010-09-07
Hola,
Tengo el mismo problema.
Tras unos días funcionando, de repente Gwibber ha dejado de funcionar. Lo he reinstalado varias veces, pero con el mismo resultado.

Estoy en  Ubuntu 10.04 x64. Si intento arrancar con el terminal, me sale esto:

** (gwibber:5394): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:5394): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:5394): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 448, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 59, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 145, in setup_ui
    self.stream_view.set_state(self.model.settings["streams"] or DEFAULT_SETTINGS["streams"])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 439, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 427, in update
    self.message_view.render([self.navigation.selected_stream["view"]])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 737, in render
    accounts=accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 279, in render
    content = template.render(theme=util.get_theme_colors(), resources=resources, _=_, **kwargs)
  File "/usr/lib/pymodules/python2.6/mako/template.py", line 133, in render
    return runtime._render(self, self.callable_, args, data)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 364, in _render
    _render_context(template, callable_, context, *args, **_kwargs_for_callable(callable_, data))
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 381, in _render_context
    _exec_template(inherit, lclcontext, args=args, kwargs=kwargs)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 414, in _exec_template
    callable_(context, *args, **kwargs)
  File "memory:0x23171d0", line 207, in render_body
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 805, in render_messages
  File "memory:0x23171d0", line 84, in message
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 317, in render_sidebar
KeyError: 'sender'

¿Alguna idea?

---

### Post by misosofos on 2010-10-02
Exactamente lo mismo por aquí.

---

### Post by alfplayer on 2010-10-02
[https://bugs.launchpad.net/gwibber/+bug/616582]("https://bugs.launchpad.net/gwibber/+bug/616582")

Parece ser este bug, todavía sin solución definitiva.

---

### Post by misosofos on 2010-10-03
A mí lo que me extraña es que en una instalación fresca y recién actualizada, sea imposible reproducir el error.

---

### Post by misosofos on 2010-10-03
Al parecer la respueta al problema, se halla en la página que Alfplayer menciona.



Having a look at the code, it seems that the facebook code for gwibber in lucid doesn't always initialise the sender part of a message to an empty dict, so if the code lower down doesn't set it then it will cause a problem (it looks like code for other systems like twitter etc always initialise the sender as blank).

To fix the problem on my system I edited:
/usr/lib/python2.6/dist-packages/gwibber/microblog/facebook.py

I found the code reading:
    if data.get("actor_id", 0) in profiles:
      m["sender"] = self._sender(profiles[data["actor_id"]])

And after it added:
    else:
      m["sender"] = {}

Unfortunately couchdb for gwibber will have cached the problem entry. I went for the easy option of clearing it out by removing the data file (as gwibber will just regrab the content). So I killed off gwibber, gwibber-service and the couchdb service and then removed:
~/.local/share/desktop-couch/gwibber_messages.couch

Starting up gwibber and everything now behaves.

---

### Post by diego826 on 2011-07-03
Hola, tengo problemas con Gwibber, no me abre para nada.. ni por 'Terminal' ni dandole un simple clic probé eliminándolo por completo, volviendo a instalar mas de 2 veces y no resultó. Desconozco bastante de Ubuntu, uso la versión 11.04 y hasta ahora me parece genial.. desinstale mi Windows 7 justo para familiarizarme con este sistema y me encontre con este problema, espero ayuda.

pd. Cuando instale ubuntu 11.04 me abría el Gwibber, vinculé mi Facebook pero no cargaba, salia todo en blanco, vi en una pagina que me recomendaban instalar Java, instale y desde ahi mi problema.

---

