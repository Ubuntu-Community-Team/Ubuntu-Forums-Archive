---
title: "Problema con gnome-lirc-propieties"
date: 2008-10-25
forum: Software
---

### Post by anarko on 2008-10-25
Cuando quiero iniciar gnome-lirc-propieties me aparece eso.
El control relejos funciona en gnome cuando aprieto las teclas escribe los numeros y el volumen sube y baja, osea el control funca, pero no puedo configurarle las teclas para usarlo con tvtime, yo toda la vida use lirc, pero ahora configuro el lirc lo inicio arranca de 10 pero el irexec no me da ni 5 de bola.

```

anarko@anarka:~$ gnome-lirc-properties 
/var/lib/python-support/python2.5/gnome_lirc_properties/__init__.py:57: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  return ui.RemoteControlProperties(gtk.glade.XML(ui_filename)).run()
WARNING:root:/usr/share/lirc/remotes: Remote Apple_A1156 listed twice in apple/lircd.conf.macmini and apple/lircd.conf.macmini.
WARNING:root:/usr/share/lirc/remotes: Remote Medion_X10 listed twice in atiusb/lircd.conf.atiusb and atiusb/lircd.conf.atiusb.
WARNING:root:/usr/share/lirc/remotes: Remote Medion_X10 listed twice in atiusb/lircd.conf.atiusb and atiusb/lircd.conf.atiusb.
WARNING:root:/usr/share/lirc/remotes: Remote DVICO_MCE listed twice in dvico/lircd.conf.fusionHDTV and dvico/lircd.conf.fusionHDTV.
WARNING:root:/usr/share/lirc/remotes: Remote BESTBUY listed twice in bestbuy/lircd.conf.bestbuy and bestbuy/lircd.conf.bestbuy2.
WARNING:root:/usr/share/lirc/remotes: Remote linux-input-layer listed twice in generic/devinput.conf and linux-input-layer-lircd.conf.
WARNING:root:/usr/share/lirc/remotes: Remote NEC listed twice in generic/NEC-pulse.conf and generic/NEC.conf.
WARNING:root:/usr/share/lirc/remotes: Remote NEC listed twice in generic/NEC-short-pulse.conf and generic/NEC.conf.
WARNING:root:/usr/share/lirc/remotes: Remote SONY listed twice in generic/SONY20.conf and generic/SONY12.conf.
WARNING:root:/usr/share/lirc/remotes: Remote PVR2000 listed twice in leadtek/lircd.conf.PVR2000 and leadtek/lircd.conf.PVR2000.
Traceback (most recent call last):
  File "/usr/bin/gnome-lirc-properties", line 27, in <module>
    gnome_lirc_properties.run(sys.argv[1:], datadir)
  File "/var/lib/python-support/python2.5/gnome_lirc_properties/__init__.py", line 57, in run
    return ui.RemoteControlProperties(gtk.glade.XML(ui_filename)).run()
  File "/var/lib/python-support/python2.5/gnome_lirc_properties/ui/RemoteControlProperties.py", line 60, in __init__
    self.__restore_hardware_settings()
  File "/var/lib/python-support/python2.5/gnome_lirc_properties/ui/RemoteControlProperties.py", line 251, in __restore_hardware_settings
    settings = lirc.HardwareConfParser(config.LIRC_HARDWARE_CONF)
  File "/var/lib/python-support/python2.5/gnome_lirc_properties/lirc.py", line 1005, in __init__
    key, value = tokens
ValueError: too many values to unpack
```

Cuestion, hay alguna otra forma de usar el control remoto de la forma que lo hace el lirc ( confogurando los botones especificos para cada aplicacion ) con el coso este que trae gnome?

PD: Bien por los desarrolladores de la 8.10 que pusieron el hack para el modulo bttv de la plaka winfast tv 2000.
PD2: Muy mal por el que se le ocurrio que los controles remotos tenian que tomarse como un teclado, muy mal.

---

### Post by anarko on 2008-10-28
Me auto respondo por si a alguien le pasa alguna vez.
Ese error es porque en /etc/lirc/hardare.conf alguno de los parametros contiene un = de mas.
En mi caso : 
REMOTE="Winfast TV2000/XP ( card=34 )"
Cuando el gnome-lirc-propieties parsea el archivo conf. del lirc parsea mal esa linea porque contiene 2 = uno para separar el parametro y otro para card=34. Solucion dejar la liena asi, total es meramente informativa esa linea.
REMOTE="Winfast TV2000/XP"

---

