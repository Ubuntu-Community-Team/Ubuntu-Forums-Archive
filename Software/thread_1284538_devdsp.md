---
title: "/dev/dsp"
date: 2009-10-06
forum: Software
---

### Post by lucasgz on 2009-10-06
hay alguna manera de detener este arhivo? (o programa nose xd)
no es nada problematico pero me pasa que cuando inicio el enemy territory tengo que reiniciarlo porque sino no hay sonido, me pasa en general cuando escucho musica tengo que pararla y esperar 1 o 2 min, o iniciar et 2 veces

 es por el siguiente error

 ------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

 pd: con el comando puedo hacer un .txt para que reinicie el dsp e inicie el juego?:P

---

### Post by pablo.s on 2009-10-06
/dev/dsp es un dispositivo. Más
especificamente, de audio. Es el
procesador digital de señal de la
placa de audio.
Si tenés que reiniciarlo es porque
tenés la configuración de ALSA
o PulseAudio de forma incorrecta,
o el juego en cuestión está utilizando
un servidor de audio que causa algún
conflicto con los antes mencionados.

---

### Post by lucasgz on 2009-10-06
no es que necesite reiniciarlo sino q tarda un poco en desocuparce y queria ver si con algun comando se puede desocupar mas rapido.
 Pero no es nada grave, yo pense que era un archivo nomas pero si es un dispositivo mejor no lo toco aver si hago q*******o:P

---

