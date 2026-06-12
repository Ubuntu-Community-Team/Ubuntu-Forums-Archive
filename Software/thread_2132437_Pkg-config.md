---
title: "Pkg-config"
date: 2013-04-04
forum: Software
---

### Post by tatu on 2013-04-04
Buenas noches para todos!! estoy tratando de instalar el Heimdall 1.3.1 para hacer un update a mi galaxy s2....lo estoy haciendo por terminal y me encuentro con esto...

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... no
configure: error: Package requirements (libusb-1.0 >= 1.0.8) were not met:

No package 'libusb-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

intente hacer extract....para redireccionar y no funciono. y no tengo idea de como configurar las variables DEPS como me sugiere...alguna sugerencia?

muchas gracias!!

saludos
TATU

---

### Post by gmunioz on 2013-04-05
Prueba con
> sudo su
apt-get install libusb libusb-dev

---

