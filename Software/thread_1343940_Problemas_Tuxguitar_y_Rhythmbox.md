---
title: "Problemas Tuxguitar y Rhythmbox"
date: 2009-12-02
forum: Software
---

### Post by marmotapl on 2009-12-02
Hola.

Hace tiempo que no tenía problemas con Ubuntu, pero lamentablemente surgió este problema cuando ejecuto Tuxguitar 1.1 y Rhythmbox 0.12.0. El asunto es que si estoy escuchando un tab en Tuxguitar y luego quiero escuchar música en el Rhythmbox, éste no funciona y tengo que cerrarlo forzadamente si es que no cierro Tuxguitar primero. Ahora si primero escucho algo en Rhythmbox y luego quiero escuchar un tab, sale un cuadro en el que dice "MIDI System is unavailable".

En la configuración de sonido de Tuxguitar, tengo puesto en Midi Sequencer: Real Time Sequencer y en MIDI Port: Java Sound Synthesizer.

Si es que alguien sabe cual es el problema por favor háganmelo saber.

Gracias de antemano (y)

---

### Post by Carlos C on 2009-12-04
¿Qué versión de Ubuntu usas?

---

### Post by marmotapl on 2009-12-11
Ahora estoy usando Jaunty... Pero tenía planeado cambiarme por este problema =\

---

### Post by moreback on 2009-12-11
Para mí que el Tuxguitar no usa PulseAudio para reproducir el sonido y por eso bloquea al Rhythmbox. La idea es que todas las apps usen PulseAudio para no bloquear la reproducción.

Revisa la configuración de sonido del Tuxguitar.

Saludos.

---

