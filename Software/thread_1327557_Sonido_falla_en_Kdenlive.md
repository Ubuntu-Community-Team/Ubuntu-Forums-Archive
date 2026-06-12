---
title: "Sonido falla en Kdenlive"
date: 2009-11-15
forum: Software
---

### Post by aledruetta on 2009-11-15
Necesito montar unos fragmentos de diversos videos con una pista de música para una presentación escolar.

Como estoy experimentando Kubuntu, que no había usado nunca (siempre Gnome), voy a usar un editor que tiene muy buena pinta: Kdenlive.

Ya ripié los videos con DVD::rip a .avi y ahora estoy por seleccionar los fragmentos para agregarles la música. 

Algunos diálogos (audio) originales deben aparecer, pero Kdenlive no está reproduciendo el audio y me da el siguiente error:

"SDL failed to open audio: No available audio device kdenlive"

Busqué en Google y está reportado el bug:

[https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/440875](https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/440875)

Ahí un usuario recomienda lo siguiente:

           Not sure it's a bug - I had the same problem and solved it by installing
 libsdl1.2debian-pulseaudio
 This removes libsdl1.2debian-alsa, but after that I had sound on kdenlive again with pulseaudio selected as audio-driver.


¿Instalo ese paquete? ¿no tendré problemas si se elimina el paquete de ALSA?

---

### Post by guillermolisi on 2009-11-15
> **aledruetta said:**
> Necesito montar unos fragmentos de diversos videos con una pista de música para una presentación escolar.

Como estoy experimentando Kubuntu, que no había usado nunca (siempre Gnome), voy a usar un editor que tiene muy buena pinta: Kdenlive.

Ya ripié los videos con DVD::rip a .avi y ahora estoy por seleccionar los fragmentos para agregarles la música. 

Algunos diálogos (audio) originales deben aparecer, pero Kdenlive no está reproduciendo el audio y me da el siguiente error:

"SDL failed to open audio: No available audio device kdenlive"

Busqué en Google y está reportado el bug:

[https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/440875](https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/440875)

Ahí un usuario recomienda lo siguiente:

           Not sure it's a bug - I had the same problem and solved it by installing
 libsdl1.2debian-pulseaudio
 This removes libsdl1.2debian-alsa, but after that I had sound on kdenlive again with pulseaudio selected as audio-driver.


¿Instalo ese paquete? ¿no tendré problemas si se elimina el paquete de ALSA?
En Kubuntu no se usa Pulse Audio, se usa Phonon, asi que no se si es una alternativa viable como solucion.

Edit: Leyendo problemas sobre audio en Kubuntu hay una alternativa que podria funcionar y no tiene riesgos:
```
rm -rf .pulse
``` que esta en tu home directory.
Cuando reinicies sesion deberia regenerarse. Como medida precautoria, renombrar/copiar ese directorio con otro nombre/en otro lugar del disco.

[Aqui hay otro thread]("http://ubuntuforums.org/showthread.php?t=1315880&highlight=kdenlive") que podria servir.

---

### Post by aledruetta on 2009-11-15
Gracias Guillermo!

Resulta que probé instalar el paquete que decía en launchpad y no funcionó. Pero cuando instalé ese paquete, el de PulseAudio, la consola me tiró varios otros paquetes como posibles instalaciones; uno de ellos en lugar de terminar en pulseaudio, alsa o oss, terminaba en all, así que lo instalé. Y funcionó. Por ahora lo dejo ahí, cualquier cosa, si deja de funcionar, hago lo que me sugerís.

---

### Post by guillermolisi on 2009-11-15
> **aledruetta said:**
> Gracias Guillermo!

Resulta que probé instalar el paquete que decía en launchpad y no funcionó. Pero cuando instalé ese paquete, el de PulseAudio, la consola me tiró varios otros paquetes como posibles instalaciones; uno de ellos en lugar de terminar en pulseaudio, alsa o oss, terminaba en all, así que lo instalé. Y funcionó. Por ahora lo dejo ahí, cualquier cosa, si deja de funcionar, hago lo que me sugerís.
Lastima no tener el nombre completo del paquete, asi se podria marcar categoricamente somo SOLVED :)

---

### Post by aledruetta on 2009-11-15
El paquete es:
```
sudo aptitude install libsdl1.2debian-all
```

---

### Post by guillermolisi on 2009-11-15
> **aledruetta said:**
> El paquete es:
```
sudo aptitude install libsdl1.2debian-all
```
> SDL is a library that allows programs portable low level access to a video
framebuffer, audio output, mouse, and keyboard.

This version of SDL is compiled with X11, aalib, and ggi graphics
drivers and oss, esound, alsa, arts, nas and pulseaudio sound drivers.
Este paquete no es Pulse Audio, solo agrega funcionalidad de acceso a bajo nivel (con el hardware) a programas multimedia como Kdenlive.

Gracias por la solucion.

---

