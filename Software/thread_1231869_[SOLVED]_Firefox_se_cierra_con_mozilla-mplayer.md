---
title: "[SOLVED] Firefox se cierra con mozilla-mplayer"
date: 2009-08-05
forum: Software
---

### Post by santiagoward2000 on 2009-08-05
Hola gente,
Por un tema del audio por el cable HDMI (otro thread) me decidí a sacar el Totem de mi máquina y usar MPlayer. Desinstalé **totem-mozilla** e instalé **mozilla-mplayer**, pero cuando quiero ver algún video en el firefox (que no sea flash) el firefox se cierra.
En la terminal lo único que sale es un **Segmentation fault**. Traté de usar la opción de debug, pero no entiendo cómo se usa gdb.
Estuve leyendo algo en internet, pero todos los errores que encontré eran por no haber desinstalado totem-mozilla (Por las dudas revisé en about:plugins y no quedó nada del totem)
Desde ya muchas gracias.
Saludos!

---

### Post by santiagoward2000 on 2009-08-06
Espero que sepan disculpar el doble post, pero encontré el [bug report]("https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/376932"). Aparentemente lo solucionaron en la versión del plugin que va a estar en karmic. Por ahora, como dicen en el report, lo solucioné instalando **gecko-mediaplayer** (preferiría no tener que instalar **gnome-mplayer**, pero anda).
Si alguien más tiene este problema, espero que les sirva.
Saludos!

---

