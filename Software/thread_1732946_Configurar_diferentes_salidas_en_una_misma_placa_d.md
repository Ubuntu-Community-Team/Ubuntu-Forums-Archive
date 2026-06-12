---
title: "Configurar diferentes salidas en una misma placa de sonido."
date: 2011-04-18
forum: Software
---

### Post by granjero on 2011-04-18
Hola, estaba leyendo la wiki del "Rivendell Open Source Radio Automation" y me encontré con que pueden configurar una placa de sonido 5.1 para que las salidas funcionen como salidas independientes.

[http://rivendell.tryphon.org/wiki/ALSA/Audigy_Multichannel_Setup](http://rivendell.tryphon.org/wiki/ALSA/Audigy_Multichannel_Setup)

El tema es que no logro entender que es lo que hacen ahí y si va a funcionar con las placas de sonido que tengo.

Alguien sabe donde puedo encontrar más data?

Salud!

---

### Post by alfplayer on 2011-04-25
Con PulseAudio se puede controlar también las salidas y las entradas.

---

### Post by granjero on 2011-05-02
Alfplayer, no le encuentro la vuelta. Alguna punta?

salud!

---

### Post by alfplayer on 2011-05-02
Me pregunto qué querés lograr exactamente, o sea, qué audio (con qué origen) querés en las salidas ?

---

### Post by granjero on 2011-05-03
Alfplayer te cuento:

Tengo un pc con una placa de sonido 5.1 

Lo que quiero lograr es que una de las salidas tome lo que reproduce "Clementine" [http://www.clementine-player.org/](http://www.clementine-player.org/)

Que otra salida tome lo que reproduce "totem"

La pc está conectada a una consola de radio. Entonces de esa manera yo tendría un canal de la consola por donde sale la música que la reproduzco con "Clementine". Y en otro canal podría tirar los efectos, separadores y los pisadores desde "totem" o "rhytmbox" y eso facilitaría mucho la operación.

La salida de la consola va al line-in de la placa para grabar lo que sale al aire.

Espero se entienda.

Saludos y Gracias!

:guitar:

---

### Post by alfplayer on 2011-05-03
Para chequear:

module-remap-sink

[http://www.pulseaudio.org/wiki/Modules#module-remap-sink](http://www.pulseaudio.org/wiki/Modules#module-remap-sink)

---

