---
title: "ayuda novato en ubuntu - video y audio"
date: 2009-02-15
forum: Software
---

### Post by sirkurt on 2009-02-15
Bueno decidi instalar ubuntu para irme familiarizando y ver si dejo de lado completamente a windows, ahora estoy teniendo varios problemas.
Tengo videos en distintos formatos especificamente mp4,avi y rmvb con los cuales tengo inconvenientes.
con los avi y mp4 tengo el problema de que se ve el video perfectamente pero no se escucha nada.
a los rvb no los puedo visualizar con ningun reproductor, los dos mencinados antes los puedo ver con vlc player pero como ya dije no puedo escucharlos.
tambien me pasa que con algunos programas como el amarrok no puedo escuchar temas en mp3.
quisiera que me indiquen como solucionar esto, ademas uso una placa de sonido que no es la de la pc es una placa de sonido usb beringher pero al parecer el sonido esta bien configurado ya que puedo escuchar musica con otros reproductores.

espero respuestas y desde ya gracias

---

### Post by Hei Ku on 2009-02-15
Tenes que instalar los codecs, como en cualquier sistema operativo. El otro dia en un XP no pude ver una peli porque no me reconocio un DVD.

Lo mas facil es entrar a Synaptic e instalarte todos los paquetes llamados gstreamer. En la parte de gestionar repositorios asegurate que tengas el repositorio multiverse habilitado, porque necesitas instalar cosas que no son libres.

---

### Post by sirkurt on 2009-02-15
justamente en eso estoy y me parece que tenes toda la razon ya que descargue un pack con ese nombre pero no de sympatic y veo que habia muchos codecs de esos sin instalar

---

### Post by sirkurt on 2009-02-15
bueno acabo de hacer lo que me dijiste, ahora esta todo perfecto con los mp4 y los avi 
el caso de los rmvb ahora puedo ver el video pero no escucho nada y con otro reproductores como el totem escucho pero no veo

---

### Post by Hei Ku on 2009-02-15
No te recomiendo que instales cosas que no sean a través de Synaptic, por seguridad. En Synaptic tenes todo lo que hace falta.

Esto no es aquel otro sistema operativo. Las cosas se hacen de otra manera.

---

### Post by sirkurt on 2009-02-15
si ya me doy cuenta 
no sabes porque puede ser que no se me escuchan los rmbv?
en realidad con pocos reproductores se me escuchan los videos no entiendo porque :S
sera cuestion de configuracion de drivers de sonido?

---

### Post by sirkurt on 2009-02-15
bueno al parecer usando la placa integrada de la computadora no hay ningun  problema  el problema es entonces la configuracion o la placa usb en si 
si conoces algun tipo de solucion avisa

---

### Post by Hei Ku on 2009-02-15
Postea en el foro de hard sobre eso. Con el resultado del comando lsusb para saber de qué placa se trata.

---

### Post by sajnox on 2009-02-15
Para los rmvb hay varias guias de como ver los archivos, pero lo que mas facil me resulto es instalar mplayer, como lo instalas ?

abris una terminal y ejecutas

```
sudo apt-get install mplayer
```

Los rmvb abrilos con mplayer, sino te andan buscar por google y cualquier problema nos avisas que te damos una mano

---

### Post by josecuervo86 on 2009-02-20
el mejor reproductor que use para rmvb es el real player, nunca tuve problemas. El mplayer no me gusto demasiado pero esos son gustos.

---

