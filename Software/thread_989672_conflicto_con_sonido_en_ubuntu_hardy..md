---
title: "conflicto con sonido en ubuntu hardy."
date: 2008-11-21
forum: Software
---

### Post by granjero on 2008-11-21
lo que sucede es lo siguiente...

si tengo el rythmbox abierto y quiero ver cualquier video en youtube o similar. el sonido de firefox no anda.

si tengo el rythmbox abierto y arranco el wine por ej con el counter strike, el counter no tiene sonido... si cierro el rythmbox y vuelvo a arrancar el counter tiene el sonido lo mas bien.. y si arranco el rythmbox ya sonando la musiquita quemante del C.S. y le doy play nunca arranca.. 

si tengo el rythmbox sonando y arranco un  video en el reproductor totem tengo ambos sonidos...

antes de reinstalar ubuntu recuerdo que jugaba al CS escuchando musica, y que aunque este el rythmbox abierto podia escuchar sonido de youtube y demases...


que sera lo que conflictua mis sonidos?

gracias por su onda infinita!

salud!

---

### Post by arielcabral on 2008-11-22
Probá lo siguiente:

Andá a Sistema->Preferencias->Sonido, luego buscar:

1.- En la pestaña "Dispositivos" probá cambiar los autodetectar por ALSA.
2.- En la pestaña "Sonidos" si tenes activada la casilla "Activar mezcla de sonidos por software".

Espero que sirva

---

### Post by granjero on 2008-11-22
cambié los autodetectar por alsa y anda joya aunque cuando pongo probar ahi en la pestaña de dispositivos estando el rythmbox reproduciendo tira este error aunque **repito anda joya ahora!**

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No se pudo abrir el dispositivo de audio para reproducción. El dispositivo está siendo usado por otra aplicación.

muchas gracias arielcabral!!!!

salud!

---

