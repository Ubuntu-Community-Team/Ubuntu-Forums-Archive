---
title: "ibus PyGI Deprecation Warning"
date: 2014-03-10
forum: Ubuntu Development Version
---

### Post by whatthefunk on 2014-03-10
Just got Kubuntu 14.04 up and running.  Everything good so far except that I cant get ibus going.  When running ibus-setup I get the following:
```
@Homebox:~$ ibus-setup
/usr/share/ibus/setup/main.py:70: PyGIDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for schema or use a class specific constructor. See: https://wiki.gnome.org/PyGObject/InitializerDeprecations
  self.__settings_general = Gio.Settings("org.freedesktop.ibus.general");
/usr/share/ibus/setup/main.py:72: PyGIDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for schema or use a class specific constructor. See: https://wiki.gnome.org/PyGObject/InitializerDeprecations
  "org.freedesktop.ibus.general.hotkey");
/usr/share/ibus/setup/main.py:73: PyGIDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for schema or use a class specific constructor. See: https://wiki.gnome.org/PyGObject/InitializerDeprecations
  self.__settings_panel = Gio.Settings("org.freedesktop.ibus.panel");
/usr/share/ibus/setup/enginecombobox.py:52: PyGIDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for schema or use a class specific constructor. See: https://wiki.gnome.org/PyGObject/InitializerDeprecations
  "org.freedesktop.ibus.general.xkblayoutconfig");
Segmentation fault (core dumped)

```

I really need to get iBus going....is there anything I can do?

---

