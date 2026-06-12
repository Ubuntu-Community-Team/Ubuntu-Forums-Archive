---
title: "Utopía: GRABAR en Ubuntu"
date: 2008-06-22
forum: Software
---

### Post by _kAz_ on 2008-06-22
Así es... algo que para mí es utópico, que me parece un imposible: que Ubuntu grabe sonido ya sea desde el mic o desde la línea de entrada.

Sinceramente no entiendo un soto, ni que es Alsa, ni que PulseAudio, o el OSS no se cuanto, así que los que me puedan dar una mano me van a tener que tener muuuuuuuuchaaaa paciencia.

Lo particular es que hasta hace unas semanas (la última vez que probé a ver si andaba algo) hacía lo de siempre: """graba""", pero a una altura minima, en audacity salen unas ínfimas líneas que hacen suponer que algo de sonido entra.

Ahora buscando info para hacerlo andar de una vez por todas encontre que instalando un tal jackd y un tal libasound2-plugins o algo por el estilo, la captura funcionaría, pero naaaaadaaaa que ver, sino por el contrario ya no pude encontrar ni siquiera esa configuración que "grababa" minimamente.

Alguien que me oriente un poquito porque no tengo ni la más mínima idea de por donde empezar siquiera.

Dejo un par de capturas.

---

### Post by pol666 on 2008-06-22
a mi es una utopia que capte el sonido..

me di uenta que en Hardy si se escucha pero BAJISIMO
 y noo transmite sonido ni en el Amsn ni grabar nada..

---

### Post by Mauro22 on 2008-06-22
Porbaste dando doble clic al controlador de volumen en el panel.

Te abre una ventana con varias solapas, 

En la segunda, tengo "grabando" y ahi me da el volumen del mic.

Luego en opciones, tendria que decir:

Input Source: mic



:confused::confused:

---

### Post by _kAz_ on 2008-06-22
> **Mauro22 said:**
> Porbaste dando doble clic al controlador de volumen en el panel.
Te abre una ventana con varias solapas, 
En la segunda, tengo "grabando" y ahi me da el volumen del mic.
Luego en opciones, tendria que decir:
Input Source: mic


Probé TODO. Debo haber probado todas las combinaciones posibles.

Ahí donde decís vos me salen diferentes opciones en Archivo > Cambiar dispositivo:
```
0: VIA 8237 (Alsa Mixer)
1: C-Media Electronics CMI9761A+ (OSS Mixer)
2: Playback: ALSA PCM on front:0 (VIA 8237) via DMA (PulseAudio Mixer)
3: Capture: Monitor Source of ALSA PCM on front:0 (VIA 8237) via DMA (PulseAudio Mixer)
4: Capture: ALSA PCM on front:0 (VIA 8237) via DMA (PulseAudio Mixer)
```

En la configuración de sonido (la imágen que puse en el post anterior), las opciones tanto en "eventos de sonido", "música y películas" como en "conferencia de sonidos" son:
```
Autodetectar
VIA8237
VIA8237 *(no entiendo por qué hay dos)*
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
Pulse Audio Sound Server

```

En Pistas predeterminadas > Dispositivos las opciones son las mismas que en el controlador de volumen (VIA, Alsa, Pulse, etc.). Y he probado que coincidan obviamente en ambos lados pero no pasa nada.

Por ejemplo el Grabador de sonidos me dice "Sus ajustes de captura de audio no son válidos. Corríjalos en los ajustes Multimedia", y toco y cambió todo de mil maneras posibles pero no pasa nada. Por caso el Audacity me sale con algo similar: "Error while opening sound device. Please check the input device settings and the project sample rate.". Pero por más que le meta mano no puedo hacer nada. :(

---

### Post by InsektO on 2008-06-22
En alsamixer, en la solapa Capture, hay que asegurarse que esté seleccionado correctamente el dispositivo de entrada para la grabación (o sea, el micrófono). Y que la barra de Captura tenga un buen nivel de volumen.

[ATTACH]75006[/ATTACH]

En general siempre está la posibilidad de aumentar un poco el volumen activando el "Mic Boost" (también está entre las opciones del alsamixer).

Otra cosa importante es no confundir al configurar el volumen del micrófono para la reproducción y para la grabación (si lo que uno graba, se escucha muy bajo, hay que subir el volumen del micrófono para la grabación, ya sea subiendo el volumen de Capture o con el "mic boost" como dije antes). El volumen del micrófono para la reproducción suele dejarse (bah, yo al menos) desactivado porque a uno no le suele interesar escuchar por los parlantes lo que va diciendo...

---

