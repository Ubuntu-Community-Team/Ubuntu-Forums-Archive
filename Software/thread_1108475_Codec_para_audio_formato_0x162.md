---
title: "Codec para audio formato 0x162"
date: 2009-03-27
forum: Software
---

### Post by euzkoarima on 2009-03-27
Buenas, tengo una peli que en 8.04 32 bits la puedo ver y escuchar lo más bien, pero en 8.10 64 bits no tiene audio.

El mplayer me tira esta info:

```
==========================================================================
ID_VIDEO_CODEC=ffwmv3
==========================================================================
Forced audio codec: mad
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound

```

Lo único que encuentro en el ubuntu de 32 que no hay en el de 64 es el paquete gstreamer0.10-pitfdll

Además despues de googlear un rato, creo (pero de seguro nada) que se debe poder ver con el realplayer

Entonces, dos cosas
1. Si alguno sabe que paquete instalar en 64 para verlo con el totem, mejor, preferiría esa.
2. Si no pruebo, con el real, ahí la pregunta es: además de la licencia, que diferencia hay entre el realplayer y el helix ?

Saludos,
Eduardo

---

### Post by pablo.s on 2009-03-27
Hola: por lo que veo de la salida de mplayer los codecs que te faltan son:

Windows Media Audio
Windows Media Audio 9

Tenés instalado el paquete w32codecs? Eeh? Di que si

Están en Medibuntu. Entre RealPlayer y Helix la diferencia creo que ninguna,
lo que si es un formato pesimo.

---

### Post by euzkoarima on 2009-03-27
> **pablo.s said:**
> Hola: por lo que veo de la salida de mplayer los codecs que te faltan son:

Windows Media Audio
Windows Media Audio 9

Tenés instalado el paquete w32codecs? Eeh? Di que si

Están en Medibuntu. Entre RealPlayer y Helix la diferencia creo que ninguna,
lo que si es un formato pesimo.

En mi caso tengo instalado el w64codecs, de medibuntu.
No se si el paquete para 64 trae menos cosas o que.

gracias,
Eduardo

---

### Post by pablo.s on 2009-03-27
> **euzkoarima said:**
> En mi caso tengo instalado el w64codecs, de medibuntu.
No se si el paquete para 64 trae menos cosas o que.

Eeemmm no, la diferencia es que w32 es para 32 bits, pero ¿no te lo reproduce
teniendo ese paquete? Y si probás con VLC ?

---

### Post by euzkoarima on 2009-03-27
nones, con vlc tampoco funciona, pero a diferencia de totem y mplayer que si funcionan en 32, vlc no me funciona (con esta peli, se entiende) ni en 32 ni en 64.

Saludos,
Eduardo

---

### Post by euzkoarima on 2009-03-27
Agrego, ya instale realplayer, y no funca con esta peli.

Slds

---

### Post by pablo.s on 2009-03-27
A ver Eduardo, vamos a probar algo que puede dar resultado:

Tratá de instalar este .deb y si funciona, funciona.

---

### Post by euzkoarima on 2009-03-27
Che, pero es para 32, el gdebi me tira un error de arquitectura al abrirlo y me deshabilita el instalar.
Entiendo que hay una manera de instalar un paquete de 32 en 64, pero no se como.

Slds

---

### Post by pablo.s on 2009-03-27
De ahi lo que necesitás realmente (de ese paquete) es gstreamer-pitfall.so
que está adentro. Lo podes descomprimir y copiar el archivo a 
/usr/lib/gstreamer-0.10 y puede que funcione, por Stallman!

---

### Post by euzkoarima on 2009-03-28
Hola, aca estoy de vuelta. Probé y no funcionó. Probe también de ponerlo en /usr/lib32 pero tampoco.
Por lo que estuve viendo parece que reproducir wm9 en 64 bits es un problema viejo aún no resuelto.
Una de las alternativas es instalar un mplayer de 32 bits, y sus montones de dependencias.
Otros prefieren instalar mplayer version windows y usarlo con wine.

Yo voy a seguir leyendo a ver si encuentor algo que me convenza. Igual esta peli que me hizo notar el "problema" me importa un bledo. Pero ver si puedo hacer andar wm9 en mi instalación de 64 bits si.

Saludos,
Eduardo

---

### Post by pablo.s on 2009-03-28
> **euzkoarima said:**
> Igual esta peli que me hizo notar el "problema" me importa un bledo. Pero ver si puedo hacer andar wm9 en mi instalación de 64 bits si.

Bueno, a mi la verdad que hacer reproducir un codec tan horrendo
como ese no me preocupa, pero como es un desafio hacerlo funcionar
traté de ayudarte de todas las maneras. Es en estos casos en los que
uno toma conciencia de la importancia de los formatos libres.
Fijate que sin instalar ningún codec se pueden ver y escuchar
en formatos como OGG y FLAC y para casi todos los demas formatos
hay que andar haciendo malabares solo porque tienen patentes.

---

### Post by euzkoarima on 2009-03-31
Pablo, en primer lugar agradezco toda la ayuda que me diste, y coincido con vos en que lo "divertido" es el desafío de hacerlo andar.

Como el tema no es importante lo tengo medio en el freezer, pero si encuentro alguna "solución elegante" la posteo.

Saludos,
Eduardo

---

### Post by pablo.s on 2009-03-31
Pregunto por curioso nomás:
¿Qué maquina estás usando?

---

### Post by euzkoarima on 2009-03-31
En el laburo tengo 8.04 32 bits, supongo que te interesa la de 64 bits, esa es :
Asus P5Q-E
Intel C2Q 9550
4Gb ram

Saludos,
Eduardo

---

