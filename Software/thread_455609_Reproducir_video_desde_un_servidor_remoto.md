---
title: "Reproducir video desde un servidor remoto"
date: 2007-05-26
forum: Software
---

### Post by loopeando on 2007-05-26
La situación es esta:

- Servidor con vídeos/musica/etc
  Windows XP

- Laptop
  Ubuntu 7.04

Hace poco que tengo este servidor (un K6-2 reciclado) y en este tengo todos mis videos y mi coleccion de mp3. El problema es que cuando quiero ver un video solo lo puedo hacer mediante Totem (GStreamer) y si quiero ver un video con subtitulos tira un error de flujo de datos.

Busco un reproductor de video que permita reproducir desde un servidor remoto con subtitulos.

Conocen alguno?

---

### Post by fetova on 2007-05-28
podrias probar xine

```
sudo aptitude install xine
```

O mplayer

```
sudo aptitude install mplayer
```

Saludos!

---

### Post by jpmorelli on 2007-05-30
Ese error de flujo de datos es muy raro, yo lo hice funcionar entrando en cada una de las solapas de preferencias y haciendo que cambiaba opciones pero dejandolas en el mismo setup y cambiando el tipo de codificación de idioma y en un momento arranca, es rarisimo !:(

---

### Post by kowal on 2007-05-30
A los mencionados por fetova sumo VLC que reproduce hasta un paty en la lectora.

```
sudo aptitude install vlc
```

Saludos.

---

### Post by loopeando on 2007-06-07
Ya probe con cuanto reproductor me cruze.

MPlayer probe, Xine probe, VLC Probe, hasta el Helix probe.

El unico con el que puedo ver los videos, pero sin subtitulos, es con el Totem (GStreamer).

Cuando quiero cargar videos con Totem con subtitulos me sigue tirando error de flujo de datos.

La configuracion esta en default porque hice una instalacion limpia hace unos dias.

¿No hay algo como el DAAP para mp3/ogg/etc pero para video y con subtitulos?

---

### Post by pablofeldman90 on 2011-10-15
Debes hacerlo con samba... ssh no puede pasar otra cosa que no sea texto...

en tu explorador de archivos
smb:/user@nombrePcRemota/ruta/al/archivo

ejecutalo con vlc no vas a tener complicaciones lo hago todo el tiempo :)

:popcorn:

---

### Post by guillermolisi on 2011-10-16
> **pablofeldman90 said:**
> Debes hacerlo con samba... ssh no puede pasar otra cosa que no sea texto...

en tu explorador de archivos
smb:/user@nombrePcRemota/ruta/al/archivo

ejecutalo con vlc no vas a tener complicaciones lo hago todo el tiempo :)

:popcorn:
ssh no puede pasar otra cosa que no sean bits.

De hecho se puede tener iniciar sesion remota de un desktop via ssh trabajando con un escritorio grafico.

[Aqui algunos resultados de una busqueda rapida en Google]("http://www.google.com.ar/search?gcx=w&sourceid=chrome&ie=UTF-8&q=desktop+vis+ssh#hl=es-419&sa=X&ei=Dl-bTsmgA-Pj0QHa5PmbBA&ved=0CBoQvwUoAQ&q=desktop+via+ssh&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=ea2e306fc45f3b1d&biw=1016&bih=614"), como para empezar.

---

