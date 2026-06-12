---
title: "Tvtime sin audio"
date: 2010-07-27
forum: Software
---

### Post by nicfer on 2010-07-27
Hola gente.

Yo estoy usando hace rato esta distro, por ahora no tuve grandes problemas, solo dos que no son muy urgentes.

Primero, tengo una placa sintonizadora de tv saa7134 y se ve excelente, lástima que no puedo hacerle andar el sonido. No tiene conectado el cable de 'loopback' (el que va de la salida de la placa a la entrada del sonido de mi pc), pero en Ventanas puedo escucharlo lo más pancho. ¿Hay algo que tenga que hacer para que el tvtime (o el sistema, no se bien dónde esta el problema) me tome el sonido directo del dispositivo? Cabe destacar que en el mezclador no aparece bajo aplicaciones el tvtime como dato adicional.

Saludos cordiales.

---

### Post by guillermolisi on 2010-07-28
La consulta sobre menu.lst en el Grub esta en [http://ubuntuforums.org/showthread.php?t=1540749](http://ubuntuforums.org/showthread.php?t=1540749)

Cada thread debe considerar un topico para facilitar su seguimiento y lograr respuestas concretas sin que se eternice en varios posts.

---

### Post by euzkoarima on 2010-07-30
Fijate en [0] en particular donde dice
> Sin Sonido

Para los que esta targeta no les da sonido doble click en el icono de sonido y habilitar la linea de entrada ademas en editar y luego preferencias y habilitar esto ademas subir el volumen y fijarse ke el altavos no este deshabilitado o en silencio

Otro link que puede ser útil es [1] , fijate donde dice
> If your Saa713x device is properly configured and still can get no sound with TVTime, you may to redirect the input source from your TV card to the output of your sound card

[0] [http://www.ubuntu-es.org/?q=node/92224]("http://www.ubuntu-es.org/?q=node/92224")
[1] [http://www.linuxtv.org/wiki/index.php/Saa7134-alsa]("http://www.linuxtv.org/wiki/index.php/Saa7134-alsa")

Saludos,
Eduardo

---

### Post by juancarlospaco on 2010-07-30
Tenes que tener el cable loopback, y que sea Stereo.

Podes conectar la salida a un minicomponente tambien, 
sino al line-in de la pc, que por defecto esta mute y Disabled.

---

### Post by nicfer on 2010-07-30
Pero no se puede sin el cable? Se que en Windows se escucha sin tener ese cable, y creo que en otro linux la hice andar así.

---

### Post by euzkoarima on 2010-07-30
Probaste con la primer opción que sugerí ?

Te adjunto mis preferencias de sonido, la idea es elegir la placa en lugar del audio interno.

No puedo probar ahora que funcione porque no estoy "al alcance" del cable de tv.

Si no logras solucionarlo, mañana a la tarde me consigo un coaxil más largo y pruebo acá.

Saludos,
Eduardo.

---

### Post by nicfer on 2010-07-31
Ya lo solucioné, con un pequeño script que me armé en base al segundo link ya me anda a la perfección.

Gracias.

---

