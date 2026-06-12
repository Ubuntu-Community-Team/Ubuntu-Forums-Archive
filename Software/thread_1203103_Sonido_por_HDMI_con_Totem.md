---
title: "Sonido por HDMI con Totem"
date: 2009-07-02
forum: Software
---

### Post by santiagoward2000 on 2009-07-02
Hola gente!
Hace mucho que vengo tratando de encontrarle la vuelta a este problema por mi cuenta, pero no llegué a nada.
Quiero conectar mi laptop a mi tele por HDMI. Tengo video, pero el sonido no se escucha cuando quiero ver algún video con Totem o reproducir algo con Listen.
Probé tanto con Alsa como OSS, y nada. Leí en varios lugares que hay que subir el volumen de IEC958 con alsamixer, pero no puedo, está la opción, pero no tiene la barrita arriba.
Lo más molesto es saber que anda, porque probé un **speaker-test** y se escuchaban los parlantes de la tele. Probé después un escuchar algo con **aplay** en la terminal y también andaba. Pero con Totem y Listen, nada.
Dejo los datos que creo pueden servir:
```
lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
```
(borré partes de la salida, como lo de la placa ethernet, pero si creen que borré algo de más, avisen y la publico entera)

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Desde ya muchas gracias.
Saludos!

_PS:_
No estaba seguro si iba acá o en Hardware. Sé que la placa se puede patear, pero como algunos sonidos se escuchan, supuse que venía por el lado del software.

---

### Post by staar on 2009-07-02
y con otro reproductor, onda vlc o mplayer?

saludos

---

### Post by santiagoward2000 on 2009-07-03
Gracias! Parece que con el Mplayer anda, y ni siquiera tuve que configurar nada. Todavía no probé el vlc. ¿Por qué será que no anda con algunos programas y otros sí?
Saludos!

---

### Post by staar on 2009-07-03
mplayer rulez! (sobre todo contra el limitado totem), supongo que será alguna configuración de gstreamer, no sé la verdad, pero para lo que vas a hacer, te conviene mplayer, tiene mejor capacidad para ese tipo de cosas...

saludos

---

### Post by sdennie on 2009-07-05
Capaz que mplayer esta usando ALSA directamente (como aplay) y totem esta tratando de usar Pulse Audio.  Fijate desde un terminal a ver cual esta usando.  Si preferis totem (Jejeje.  Me da risa en pensarlo) y el problema es ALSA/Pulse, podes cambiar totem a usar ALSA.

---

### Post by ariel on 2009-07-05
> **santiagoward2000 said:**
> Hola gente!
Hace mucho que vengo tratando de encontrarle la vuelta a este problema por mi cuenta, pero no llegué a nada.
Quiero conectar mi laptop a mi tele por HDMI. Tengo video, pero el sonido no se escucha cuando quiero ver algún video con Totem o reproducir algo con Listen.
Probé tanto con Alsa como OSS, y nada. Leí en varios lugares que hay que subir el volumen de IEC958 con alsamixer, pero no puedo, está la opción, pero no tiene la barrita arriba.
Lo más molesto es saber que anda, porque probé un **speaker-test** y se escuchaban los parlantes de la tele. Probé después un escuchar algo con **aplay** en la terminal y también andaba. Pero con Totem y Listen, nada.
Dejo los datos que creo pueden servir:
```
lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
```(borré partes de la salida, como lo de la placa ethernet, pero si creen que borré algo de más, avisen y la publico entera)

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Desde ya muchas gracias.
Saludos!

_PS:_
No estaba seguro si iba acá o en Hardware. Sé que la placa se puede patear, pero como algunos sonidos se escuchan, supuse que venía por el lado del software.


Mi configuracion es un poco distinta, yo uso hdmi para video solo, y para audio uso la salida digital spdif del motherboard conectada a un amplificador. Por lo que vos decis al parecer audio por hdmi se configura igual que spdif (iec958). Yo uso pulseaudio y tuve que luchar un poquito para hacer andar esta configuracion, pero anda barbara, sobre todo con 9.04. Las notas que siguen te pueden dar un pista de para donde apuntar.

   - Pulseaudio
       Uses alsa drivers / sinks, only replacing the mixer and ESD server
       Volume controls: sudo apt-get install pavucontrol
       Digital output (only analog shown by default, even if alsa / aplay -l shows both analog and digital)
           - added the following line to /etc/pulse/default.pa: 
               load-module module-alsa-sink device=hw:0,1      ## Card 0, Device 1
               may also work: load-module module-alsa-sink device=spdif:0
           - Kill and restart the audio server:
               pulseaudio -k
               pulseaudio -D
           - IEC958 flag in alsamixer needs to be activated
        Mplayer and mplayer-plugin: use the "pulse" audio output (even if not listed in the plugin)
           - iecset audio true  (man iecset)

---

