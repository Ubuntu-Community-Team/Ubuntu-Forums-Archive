---
title: "Falta de sonido al reiniciar"
date: 2009-10-30
forum: Software
---

### Post by ubnix on 2009-10-30
Hola a todos, quisiera ver si me pueden dar una manito.
Nosé que habrá pasado que hoy encendi mi pc y dejo de andar el sonido, no del todo, por ejemplo reproduce sonido una pagina online. Pero al reproducir musica no pasa nada.
En sistema>preferencia>sonido me marca como que todo esta bien, pero al querer hacer pruebas de sonido no se escucha nada.
Alguien sabe que puede ser??
Gracias!

---

### Post by BlackHero on 2009-10-30
hola, proba tipeando esto en la consola

cat /proc/asound/modules

decime que te muestra.

y despues proba recargando alsa

sudo /sbin/alsa force-reload

---

### Post by guillermolisi on 2009-10-30
> **BlackHero said:**
> hola, proba tipeando esto en la consola

cat /proc/asound/modeules

decime que te muestra.

y despues proba recargando alsa

sudo /sbin/alsa force-reload
Sera que quisiste poner ```
cat /etc/asound/**modules**
``` ?

---

### Post by guillermolisi on 2009-10-30
> **ubnix said:**
> Hola a todos, quisiera ver si me pueden dar una manito.
Nosé que habrá pasado que hoy encendi mi pc y dejo de andar el sonido, no del todo, por ejemplo reproduce sonido una pagina online. Pero al reproducir musica no pasa nada.
En sistema>preferencia>sonido me marca como que todo esta bien, pero al querer hacer pruebas de sonido no se escucha nada.
Alguien sabe que puede ser??
Gracias!
Por casualidad, actualizaste la version de Ubuntu que estabas usando ?

Probaste en una terminal/consola ingresar "alsamixer" (sin las comillas) y revisar ahi que no tengas ningun canal silenciado y los controles de volumen arriba ?

---

