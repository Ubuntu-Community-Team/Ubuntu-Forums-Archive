---
title: "[SOLUCIONADO] Audacious y crossfade (fundido de canciones)"
date: 2010-08-10
forum: Software
---

### Post by gothman7 on 2010-08-10
Buenas tardes:

LLevo como una semana con ubuntu, primero 9.10 y hace como 3 días actualice a 10.04.
Ha sido una semana de investigación, pegado al laptop, pero creo que ya lo tengo como me gusta de acuerdo a mis necesidades y con similares herramientas con las que trabajaba en windows. El primer desafío fue instalar la famosa inalambrica broadcom, sin contar con internet, pero lo logré.

Bueno despues de tanto rodeo... hay solo algo que me complica, buscando reproductores de audio llegue al audacious (2.3), que tiene todas las caracteristicas que buscaba, atajo de teclado multimedia, un atajo para saltar a la cancion que yo quiera dentro de la playlist actual, lo unico que me falta es el fundido entre las canciones, crossfade, ya que en las configuraciones de sonido del reproductor pongo el plugin de crossfade, pero las canciones bajan su velocidad de reproducción, cosa que no sucede con los otros plugins de salida.

que podra ser?... para el sonido de la maquina en general tengo instalado el pulseaudio equalizer, por si sirve como dato.

Mi pc es un presario M2000 con una conexant ac' 97

---

### Post by Patriciologico on 2010-08-10
El sonido de audacious con que salida esta? ejecutalo en consola, para ver si te manda algun mensaje cuando se funden las canciones.

---

### Post by gothman7 on 2010-08-11
Hola!

Bueno para que funcione el crossfade, hay que seleccionar la salida de "crossfade plugin", que es la que me da problema, cualquiera de las otras salidas el funcionamiento es normal. Por cierto dentro de la salida "crossfade plugin" en su configuración, se elige nuevamente el plugin de salida, he probado todos y el resultado es el mismo, baja velocidad de reproducción.

Con respecto a la ejecucuón en terminal, la orden sería "sudo audacious2". Si es asi el reproductor se ejecuta bien no muestra ningun error la consola, pero se sigue escuchando la reproducción con el tempo bajisimo, o sea que cantan como robots.

seguiré esperando, mañana desinstalaré el reproductor completamente y lo reinstalaré a ver si se soluciona.

Pd: gracias por tu respuesta

---

### Post by themasterdark on 2010-08-11
Para que veas si arroja problemas ejecutalo en consola solo como 

audacious2 

sin el sudo ya que de esa forma lo estas ejecutando como administrador (root)

Saludos =)

---

### Post by gothman7 on 2010-08-11
Hola

Esto sale con el plugin activado

gothman@gothman-pc:~$ audacious2
madplug: bad main_data_begin pointer.
madplug: bad main_data_begin pointer.


Y antes salio un mensaje parecido pero con un numero y la palabra frame, pero de tonto cerre la terminal y no lo alcance a copiar. Y no apareció de nuevo.

Gracias

---

### Post by gothman7 on 2010-08-11
ahi apareció:

madplug: Skipping 417 bytes over broken frame

Salu2

---

### Post by gothman7 on 2010-08-12
Finalmente desinstale todo desde Synaptic, borre la carpeta de configuración y reinstalé.

Ahora si funciona, aunque si le cambio algunas opciones al plugin, vuelve a lo mismo, asi que dejandolo como viene por defecto funciona bien.

Doy el asunto por solucionado

No se como se editará el tema para poner solucionado en el titulo

Gracias por todo

---

