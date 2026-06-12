---
title: "Desfasaje entre Audio y Video"
date: 2009-04-29
forum: Software
---

### Post by Peter Smile on 2009-04-29
Muchachos, la verdad es que ya he probado todo lo que se me ocurrió (google incluído) y no encontré una solución por eso acudo a uds como mi salvación, paso a la cuestión:

Desde que instalé Jaunty (AMD64) he tenido algunos problemas con los videos, el inconveniente es que en algún punto aleatorio de la reproducción la imagen se congela unos instantes y el audio continúa normalmente, lo que produce un desfajase entre ambos. Esta desincronización dura cuando mucho un minuto, luego la imagen se acelera hasta que alcanza al audio, y continúan juntos unos minutos más hasta que vuelve a ocurrir. Es realmente muy molesto.

El problema no parece suceder principalmente con un tipo de video en particular, pues ocurre con los FLV, los MPEG-4 y los de Youtube (que creo que son FLV).

En la máquina tengo dos particiones, una con el directorio **/** (raíz) montado (ext 4) y otra, que perdura desde hardy, con el **/home** montado (ext 3).

Los codecs instalados son: **Base**, **Good**, **Ugly** y **Fluendo** (probé instalar **Bad**, y tengo el mismo problema).

Los reproductores que he probado son: **VLC**, **Totem**, **Xine**, **SMPlayer** y **Mplayer** (Que me da un error de actualización pero anda bien).

A los archivos en sí mismos los descarto porque este problema no ocurre siempre en el mismo punto, además a algunos de ellos los reproducía sin problemas con intrepid.

Les agradezco desde ya,

Peter Smile

---

### Post by Peter Smile on 2009-04-29
**Actualización:**
He creado un usuario nuevo, y en la configuración de ese usuario no hay problemas. Obviamente es un inconveniente de configuración por mantener la misma carpeta **home** de Intrepid.

Solamente me falta encontrar la configuración de Gstreamer en mi carpeta personal.

---

### Post by Tosh78 on 2009-04-30
Hola! Me paso lo mismo que a vos, solo que yo habia hecho una instalacion limpia. Yo lo solucione seteando el sonido en ALSA. Fijate como lo tenes configurado.

---

### Post by Peter Smile on 2009-05-04
A mí no me sirvió pasarlo a ALSA, de hecho me fue peor porque a los reproductores de audio se les cortaba el sonido; tuve que ponerlo en Pulse.

Más allá de eso, lo solucioné eliminando todos los archivos de configuración de gstreamer y xine. No puedo asegurar cual de los dos daba problemas, o si eran ambos.

Simpremente borré las carpetas .xine y .gstreamer-0.10 de mi carpeta personal y santo remedio.

---

