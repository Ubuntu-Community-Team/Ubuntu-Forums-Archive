---
title: "Gtk+-2.18"
date: 2009-10-12
forum: Software
---

### Post by Fonola on 2009-10-12
resulta que quiero instalar éste GTK

el problema es al intentar compilarlo.

me sale lo siguiente:
```

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.21.3    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Requested 'glib-2.0 >= 2.21.3' but version of GLib is 2.20.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

resulta que tengo descompresas y compiladas las librerías:

glib-2.22.2
pango-1.26.0

que son las mismas librerías que presenta el sitio de GTK

[http://www.gtk.org/download-linux.html](http://www.gtk.org/download-linux.html)

Alguien me podría hacer un resumen en español para saber como instalar las librerías correctamente y así conseguir sin problemas compilar gtk+-2.18.2

Saludos!

PD: Distro Ubuntu 9.04 Desktop Edition (Original)

---

