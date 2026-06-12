---
title: "Posible problema de placa de video, ubuntu 10.04"
date: 2010-12-14
forum: Software
---

### Post by sanson222 on 2010-12-14
Bueno, holas a toda la comunidad, hace mucho que no tenia un problema con ubuntu pero de la nada ahora tengo un problema.

Actualize desde 9.04 a 9.10 y luego a 10.04, no habia ningun problema e incluso utilize 10.04 por un largo tiempo sin problema.

El problema aparecio de la nada, estaba usando mi ubuntu cuando quise abrir el firefox, me salia la ventana de que debia reiniciar firefox, pero no se vei nada dentro de esta, tambien pasaba cuando abria carpetas o cualquier programa.
Probe reiniciando para ver si se arreglaba, luego veo que despues de la seleccion de grub la pantalla se pone negra, me doy cuenta de que esta cargando ubuntu porque la camara muestra actividad, luego escucho el ruido que ubuntu hace para seleccionar usuario, aqui la pantalla es un poco rara, se ven rayas arriba de la pantalla, como si fueran los driver de la placa de video.
Probe en modo recovery para ver que podia hacer, pero sigue igual, aparecen esas rayas de colores en la parte superior de la pantalla.
Lo ultimo que hize fue actualizar unas actualizacion de ubuntu.

Especificaciones de mi maquina:
disco compartido:
win xp 70Gb ubuntu 75 GB
DDR2 1GB
nforce 405 geforce 6100 "on board"
amd sempronm 3200+

si alguien me puede sugerir que hacer se lo agredeceria.

---

### Post by hectorivand on 2010-12-15
> **sanson222 said:**
> Bueno, holas a toda la comunidad, hace mucho que no tenia un problema con ubuntu pero de la nada ahora tengo un problema.

Actualize desde 9.04 a 9.10 y luego a 10.04, no habia ningun problema e incluso utilize 10.04 por un largo tiempo sin problema.

El problema aparecio de la nada, estaba usando mi ubuntu cuando quise abrir el firefox, me salia la ventana de que debia reiniciar firefox, pero no se vei nada dentro de esta, tambien pasaba cuando abria carpetas o cualquier programa.
Probe reiniciando para ver si se arreglaba, luego veo que despues de la seleccion de grub la pantalla se pone negra, me doy cuenta de que esta cargando ubuntu porque la camara muestra actividad, luego escucho el ruido que ubuntu hace para seleccionar usuario, aqui la pantalla es un poco rara, se ven rayas arriba de la pantalla, como si fueran los driver de la placa de video.
Probe en modo recovery para ver que podia hacer, pero sigue igual, aparecen esas rayas de colores en la parte superior de la pantalla.
Lo ultimo que hize fue actualizar unas actualizacion de ubuntu.

Especificaciones de mi maquina:
disco compartido:
win xp 70Gb ubuntu 75 GB
DDR2 1GB
nforce 405 geforce 6100 "on board"
amd sempronm 3200+

si alguien me puede sugerir que hacer se lo agredeceria.

Hola, la actualización también fue sobre el Kernel? te digo esto porque tuve algunos problemas después de actualizar a la última versión. Ojo, estoy en 10.10.

Otra cosa, probaste reinstalando los drivers de video?

Saludos
Nacho

---

### Post by sanson222 on 2010-12-15
Primero que nada gracias.
El kernel si lo actualize, en este momento no te podria dar la version pero se que lo actualize por que tube problemas con el sonido. Bueno sobre reinstalando los driver de video, no veo como a menos que se pueda hacer por un live cd, si es posible me podrias decir como seria?

---

### Post by EnriqueK on 2010-12-15
Fijate en este enlace 
[http://www.distrotest.es/?p=5349](http://www.distrotest.es/?p=5349)

---

### Post by sanson222 on 2010-12-17
creo que no me entendieron, no puedo acceder a ubuntu, cuando entro toda la pantalla esta negra pero se puede escuchar el sonido cuando aparece la ventana de login, tampoco puedo por terminal, nose porque pero no se ve nada.
Voy a probar que puedo hacer y pruebo que pasa con el live cd, si se les ocurre alguna solucion les agradeceria

---

### Post by granjero on 2010-12-18
hola, en el grub elegí de bootear con el kernel anterior a ver que pasa...

salud!

---

### Post by sanson222 on 2010-12-18
Es lo primero que hice, probe con el antiguo kernel pero aun asi no pasa nada, cuando entro en terminal (ctrl+alt+F1) solamente se ven unas rayas arriba, cuando escribo se mueven. Yo crei que los driver no tenian que ver cuando estabas en modo terminal >_>.

---

### Post by sanson222 on 2010-12-21
Bueno un amigo me recomendo que tenia que iniciar en modo seguro de video o algo asi, le dije que no tenia esa opcion en el grub y el me respondio que eso lo tenes que habilitar cuando vas a instalar ubuntu, asi que mi pregunta es esta.
Se puede reinstalar ubuntu sin perder los datos pero que la carpeta /home no este en una particion diferente? opte por esto por que no se me ocurre nada y ya hace una semana que estoy sin ubuntu.

---

