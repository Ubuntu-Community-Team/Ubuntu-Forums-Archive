---
title: "Talvez a alguien le ayuda"
date: 2008-09-01
forum: Software
---

### Post by katon on 2008-09-01
Aqui les comento algo que me funciono a mi perfecto para ver Video streaming en protocolo MMS de Microsoft , en la universidad donde estudio para ver clases online, son instrucciones para utilizar el VLC:

lo mas importante el primer paso 

[SIZE="4"](1) buscar e instalar en synaptic ffmpeg  and liveMedia (live555) [/SIZE]
 
(2) install : vlc
    de ser necesario : 
    vlc deberia ser compilado con --enable-ffmpeg and --enable-live555 flags    (lo cual es por defecto).

 
(3) cambia el url de la pelicula  "mms://" a "rtsp://" 
 
(4) correr vlc usando el parametro  --rtsp-tcp ( esto esta en uno de los menus tambien en la version grafica seleccionar rtsp protocol)
 

a mi me funciono al instante.

---

### Post by faktorqm on 2008-09-02
esto es solo para video? yo al menos lo probe y se me cierra el vlc :( a vos te anda bien?

---

### Post by katon on 2008-09-02
a mi me anda bien
y eran videos con audio..

---

