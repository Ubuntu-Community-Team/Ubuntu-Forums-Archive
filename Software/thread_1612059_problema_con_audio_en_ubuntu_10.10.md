---
title: "problema con audio en ubuntu 10.10"
date: 2010-11-02
forum: Software
---

### Post by hetitor on 2010-11-02
buenas tardes les escribo para ver si pueden darme una mano, cada tanto mientras escucho musica, se me corta la reproduccion y me sale el siguiente mensaje:
**[COLOR=Black]pa_stream_writable_size() failed: Conexión finalizada[/COLOR]**
estuve buscando pero no he encontrado algo que me pueda ayudar, los saludo esperando su respuesta.

---

### Post by hectorivand on 2010-11-03
> **hetitor said:**
> buenas tardes les escribo para ver si pueden darme una mano, cada tanto mientras escucho musica, se me corta la reproduccion y me sale el siguiente mensaje:
**[COLOR=Black]pa_stream_writable_size() failed: Conexión finalizada[/COLOR]**
estuve buscando pero no he encontrado algo que me pueda ayudar, los saludo esperando su respuesta.

Hola Hetitor, bienvenido, la música que escuchas esta alojada en un servidor u otro equipo de la red?

Pregunto, porque no tiene mucho sentido y mis disculpas si me equivoco que falle la "conexión" si tenes la música en la computadora de manera local

Saludos
Nacho

---

### Post by hetitor on 2010-11-04
hola hectorivand, gracias por la pronta respuesta, te cuento que la musica la tengo en pc local, no a travez de un servidor, espero puedas ayudarme
te saludo desde ushuaia.

---

### Post by hectorivand on 2010-11-04
> **hetitor said:**
> hola hectorivand, gracias por la pronta respuesta, te cuento que la musica la tengo en pc local, no a travez de un servidor, espero puedas ayudarme
te saludo desde ushuaia.

¿Qué reproductor de audio usas?

Bugs reportados del problema... con Totem.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/417976](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/417976)

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/532586](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/532586)

Para música te recomiendo Rhythmbox o Amarok. Los instalas con el siguiente comando.:

```
sudo apt-get install rhythmbox
```

```
 sudo apt-get install amarok
```

Contame si lo pudiste resolver con esto...

Saludos
Nacho

---

### Post by hetitor on 2010-11-13
hola perdon por tardar en contestar, he tenido problemas de internet, te cuento que uso el repdroductor Exaile, con amarok, tambien me lo hace, lo curioso es que por ejemplo estoy escuchando una lista de repdroduccion con 30 temas y todo bien, pasan los dias vuelvo a escuchar y en cualquier momento se me corta y sale el cartel.
la verdad la primera vez que me pasa
te mando un saludo desde tierra del fuego

---

### Post by hectorivand on 2010-11-15
No te pasa siempre, es aleatorio?

Tal vez hay problemas con los drivers de sonido, la música o cuando subís y bajas el volumen, no salen con ruido?

Te aconsejo que instales estás librerías, en algunas aplicaciones, tenía problemas con la reproducción, lo instale, la seleccione y santo remedio.:

```
sudo apt-get install libportaudio2
```

Contame como sigue.

Saludos
Nacho

---

### Post by elcangrejoviajero on 2011-12-25
Hola. Feliz Navidad antes que nada :) Yo tambièn tengo el mismo problema con Ubuntu 11.10. No tengo audio. Ya probè con distintos reproductores y con las soluciones que han descrito antes pero nada. Antes, tenìa el Ubuntu 10.04 y no me pasaba esto. Ahora lo actualicè a la versiòn mencionada y me pasa.saludos.

---

