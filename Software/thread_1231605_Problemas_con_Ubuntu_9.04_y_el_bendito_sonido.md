---
title: "Problemas con Ubuntu 9.04 y el bendito sonido"
date: 2009-08-04
forum: Software
---

### Post by energia_positiva on 2009-08-04
Hola muchachos, les he estado siguiendo desde hace tiempo para poder asesorarme e instalar el Ubuntu  32-bit (gracias a dios, nunca me arrepentiré de haberlo instalado :D), pero tengo una situacion en la cual, he revisado casi todos los threads y he hecho todo todo tooodoo lo que he podido hacer y no he logrado poder escuchar mas que RUIDOS en mi ubuntu, ruidos como de cuando se esta conectando un microfono. (ojo no tengo mic)

Mi Hardware es:

Tarjeta Madre Asrock Wolfdale 1333.D667, Pentium 4 3.2Ghz extreme edition, 3 GB de ram, 250 disco duro, tarjeta de video Geforce 8400GS de 512.

Sonido Integrado, y mis cornetas son unas Logitech 2.1.

Estas cornetas no traen drivers, y bueno en mi particion de Xp, (tengo los dos sistemas operativos a pesar de todo, de todas maneras de lo malo de windows, el Xp es el mejorsito) y nunca me ha creado problemas por ahi.

¿Que podria ser?

---

### Post by guillermolisi on 2009-08-05
> **energia_positiva said:**
> Hola muchachos, les he estado siguiendo desde hace tiempo para poder asesorarme e instalar el Ubuntu  32-bit (gracias a dios, nunca me arrepentiré de haberlo instalado :D), pero tengo una situacion en la cual, he revisado casi todos los threads y he hecho todo todo tooodoo lo que he podido hacer y no he logrado poder escuchar mas que RUIDOS en mi ubuntu, ruidos como de cuando se esta conectando un microfono. (ojo no tengo mic)

Mi Hardware es:

Tarjeta Madre Asrock Wolfdale 1333.D667, Pentium 4 3.2Ghz extreme edition, 3 GB de ram, 250 disco duro, tarjeta de video Geforce 8400GS de 512.

Sonido Integrado, y mis cornetas son unas Logitech 2.1.

Estas cornetas no traen drivers, y bueno en mi particion de Xp, (tengo los dos sistemas operativos a pesar de todo, de todas maneras de lo malo de windows, el Xp es el mejorsito) y nunca me ha creado problemas por ahi.

¿Que podria ser?
En una terminal/consola ingresa el comando "lspci" y mostranos la salida que te devuelve. Con eso vamos a saber que detecta Ubuntu en tu maquina.

Tambien corre "lsmod" y mostranos su salida, asi sabremos si los modulos de audio se cargan y si son los correctos.

---

