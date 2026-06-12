---
title: "Inicio sin sonido"
date: 2009-06-11
forum: Software
---

### Post by Fernando Gonzalo Pellico on 2009-06-11
Buenas tardes a todos.

Les cuento: Como tenía problemas con el Skype, actualicé el alsa a la última versión, a la 1.0.20, compilando y demás. Se solucionó el problema y se notan las mejoras, ciertamente, pero ahora cuando inicio la PC, aparece siempre el sonido en mute. Aunque cambie la configuración y la guarde, el sonido está siempre en mute.

Datos: Uso Jaunty 9.04, tengo el PulseAudio actualizado a la 1.0.9.15 y el alsa a 1.0.20. Es sólo al iniciar la PC, pero es bastante molesto, si conocen alguna solución, les agradecería.

Un saludo

---

### Post by staar on 2009-06-11
con que herramienta cambias el volumen? la de pulseaudio, la de gnome, con alsamixer? tenés en tu sistema un archivo /etc/asound.state?

saludos

---

### Post by Fernando Gonzalo Pellico on 2009-06-11
Con la de Gnome, en el panel superior. Tengo el archivo que dices. Se solucionaría editando los valores a mano en ese archivo?

---

### Post by staar on 2009-06-11
no es necesario que sea a mano, hacé lo siguiente, en una Terminal corré ```
alsamixer
``` y seteá el volumen como desees, despues salí (con Alt + Q) y poné ```
sudo alsactl store
``` para estar seguros, después andá a Sistema > Preferencias > Sesiones y añadí una entrada (con el nombre que quieras) y en comando poné este ```
alsactl restore
```

saludos

---

### Post by Fernando Gonzalo Pellico on 2009-06-11
Parece que funcionó!

Muchas Gracias.

Un saludo

---

### Post by aledruetta on 2009-06-27
> **Fernando Gonzalo Pellico said:**
> Buenas tardes a todos.

Les cuento: Como tenía problemas con el Skype, actualicé el alsa a la última versión, a la 1.0.20, compilando y demás. Se solucionó el problema y se notan las mejoras, ciertamente, pero ahora cuando inicio la PC, aparece siempre el sonido en mute. Aunque cambie la configuración y la guarde, el sonido está siempre en mute.

Datos: Uso Jaunty 9.04, tengo el PulseAudio actualizado a la 1.0.9.15 y el alsa a 1.0.20. Es sólo al iniciar la PC, pero es bastante molesto, si conocen alguna solución, les agradecería.

Un saludo

Yo resolví el problema de Skype usando una versión que está en los repositorios de medibuntu y que usa oss en lugar de Pulse o Alsa.

Pregunta ¿cómo se actualiza alsa y PulseAudio?

---

