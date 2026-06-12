---
title: "UbuntuOne en Xubuntu Lucid"
date: 2010-05-02
forum: Software
---

### Post by santiagoward2000 on 2010-05-02
Hola gente!
Tengo un problema con **ubuntuone-client-gnome** desde que instalé Lucid. No puedo abrirlo, y cuando ingreso **ubuntuone-preferences** en una terminal me tira el siguiente error:
> Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 1146, in <module>
    prefs_dialog = UbuntuOneDialog()
  File "/usr/bin/ubuntuone-preferences", line 538, in __init__
    self.__construct()
  File "/usr/bin/ubuntuone-preferences", line 978, in __construct
    self.devices.list_devices()
  File "/usr/bin/ubuntuone-preferences", line 382, in list_devices
    fsync_enabled = self.sdtool.is_files_sync_enabled()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 708, in is_files_sync_enabled
    return get_user_config().get_files_sync_enabled()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/config.py", line 148, in wrapped
    return meth(self, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/config.py", line 321, in get_files_sync_enabled
    return self.get_parsed(MAIN, 'files_sync_enabled')
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/config.py", line 266, in get_parsed
    return self.default.get(section, option).value
  File "/usr/lib/python2.6/ConfigParser.py", line 311, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: '__main__'

¿Alguna idea de qué puede ser?
Saludos!

_EDIT:_
Al final pude conectarme por medio de u1sdtool. En caso de que alguien más tenga este problema, lo que hice fue instalar **ubuntuone-client-tools**. Después, desde una terminal:
```
u1sdtool --start
u1sdtool -c
```
Ahí se abrió el navegador para conectarme y agregar esta máquina.
Puedo intercambiar archivos con el servidor. Ahora lo único que me falta es el ícono y las notificaciones. ¿Puede ser que esto se deba a que ahora UbuntuOne está integrado al MeMenu de GNOME?
Saludos!

---

### Post by xcristi on 2010-05-03
Unfortunately I don't speak Spanish, but if you end up with an error like that, go to the /usr/share/xubuntu/session.sh file and comment out the lines with export XDG:

```

#export XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu
#export XDG_DATA_DIRS=/etc/xdg/xdg-xubuntu
exec startxfce4

```
The bug is spotted [here]("https://bugs.launchpad.net/ubuntu/lucid/+source/xubuntu-default-settings/+bug/571133").

---

### Post by santiagoward2000 on 2010-05-03
> **xcristi said:**
> Unfortunately I don't speak Spanish, but if you end up with an error like that, go to the /usr/share/xubuntu/session.sh file and comment out the lines with export XDG:

```

#export XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu
#export XDG_DATA_DIRS=/etc/xdg/xdg-xubuntu
exec startxfce4

```
The bug is spotted [here]("https://bugs.launchpad.net/ubuntu/lucid/+source/xubuntu-default-settings/+bug/571133").

Thanks a lot xcristi! That did it :D

---

