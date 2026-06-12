---
title: "No me conecto a internet con Ubuntu 9.04"
date: 2009-08-07
forum: Software
---

### Post by Tio Bill on 2009-08-07
Habia instalado la version 8.04 de ubuntu a la cual con** pppoeconf dsl-provider** habia logrado conectarme a internet sin ningun inconveniente, pero ahora que formatee e instale el CD Live de la version 9.04 no logro conectarme a internet aunque haya seguido los mismos pasos. Cuando pongo **ifconfig pppo** sale lo siguiente:                                                                                                   [B]dermadroid@dermadroid-desktop:~$ sudo pon dsl-providerPlugin rp-pppoe.so loaded.RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5/usr/sbin/pppd: In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-dsl-provider-provider-provider-provider'                                                                  
dermadroid@dermadroid-desktop:~$ ifconfig pppo
pppo: error al obtener información sobre la interfaz: Dispositivo no encontrado[/B]                                                            [LEFT]Espero sus consejos.Tengo un modem ZTE zxdsl 831, el que provee telefonica.[/LEFT]

---

### Post by sitodonosti on 2009-08-07
que tarjeta de internet tienes?prueba a ponr lspci para ver si te lo detecta el sistema

---

### Post by guillermolisi on 2009-08-07
Y si ese modem se conecta via USB, en lugar de "lspci" corresponderia "lsusb"

---

### Post by Tio Bill on 2009-08-07
Bueno al final pude conectarme pero lo tuve que hacer formateando e instalando todo de nuevo, cosa que no requiere mucho tiempo y como todavía no había hecho modificaciones no me molestaba. Gracias por su tiempo. Así que se puede dar por solucionado.

---

### Post by guillermolisi on 2009-08-07
> **Tio Bill said:**
> Bueno al final pude conectarme pero lo tuve que hacer formateando e instalando todo de nuevo, cosa que no requiere mucho tiempo y como todavía no había hecho modificaciones no me molestaba. Gracias por su tiempo. Así que se puede dar por solucionado.
Antes de dar el thread por solucionado, actualiza el sistema a fondo, es decir todos los paquetes que tengas pendientes, y volve a probar despues de reiniciar. Si sigue funcionando, entonces si con gusto lo etiqueto como solucionado.

---

### Post by Tio Bill on 2009-08-08
> **guillermolisi said:**
> Antes de dar el thread por solucionado, actualiza el sistema a fondo, es decir todos los paquetes que tengas pendientes, y volve a probar despues de reiniciar. Si sigue funcionando, entonces si con gusto lo etiqueto como solucionado.
Estimado Guillermo, cuanta razón en tus palabras, no hice mas que actualizar y reiniciar que ya perdí la conexión nuevamente. Pero eso ahora es un problema de menor importancia. Voy a abrir otro tema al respecto para no desvirtuar este thread, y agradecería infinitamente tus consejos.

---

### Post by guillermolisi on 2009-08-08
Cuando estes de nuevo "en carrera" seguimos con este tema.

---

