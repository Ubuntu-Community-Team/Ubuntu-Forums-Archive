---
title: "No se me abre el LISTEN nuevo en karmic"
date: 2009-10-31
forum: Software
---

### Post by nahuel_89p on 2009-10-31
Cuando intento ejecutar el listen, la consola me devuelve esto:

> /home/nahuel/.themes/Dust Burnt/gtk-2.0/gtkrc:602: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/nahuel/.themes/Dust Burnt/gtk-2.0/gtkrc:603: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/lib/pymodules/python2.6/musicbrainz2/model.py:21: DeprecationWarning: the sets module is deprecated
  from sets import Set

Parece que lo importante es lo del musicbrainz2, que sin embargo lo tengo isntalado en synaptic. Probe reinstalando todo, pero aun asi, no funciona nada.


Y en modo sudo, me devuelve esto:

> AttributeError: 'module' object has no attribute 'Element'                                                                                     
/usr/lib/pymodules/python2.6/musicbrainz2/model.py:21: DeprecationWarning: the sets module is deprecated                                       
  from sets import Set                                                                                                                         
Traceback (most recent call last):                                                                                                             
  File "listen", line 200, in <module>                                                                                                         
    ListenApp()                                                                                                                                
  File "listen", line 141, in __init__                                                                                                         
    self.option.run_load()                                                                                                                     
  File "/usr/lib/listen/option_parser.py", line 113, in run_load
    obj = bus.get_object("org.gnome.Listen","/org/gnome/listen")
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
nahuel@nahuel-desktop:~$


Gracias

---

### Post by nahuel_89p on 2009-11-01
Problema resuelto, hay que borrar los directorios /.cache/listen and /.config/listen..
Pero la biblioteca me nombra mal las canciones, muchas aparecen tituladas como file://media/disk/... y cosas asi. Alguna idea para solucionar esto?

---

### Post by nahuel_89p on 2009-11-01
mas problemas... la verdad es que necesitaria una solucion general, osea, solucionando los problemitas no hago nada... no es como tener que borrar los directorios de config y cache cada vez q reinicio la pc, y encima volver a cargar la biblioteca. Haria falta una version nueva, bugfix... 
A alguien mas le paso esto?

---

