---
title: "Problema con Amarok2 en Ubuntu 9.04, no suena"
date: 2009-06-16
forum: Software
---

### Post by Tenisfan on 2009-06-16
Hola amigos del foro, otra vez recurro a su ayuda. Resulta que quise probar el reproductor Amarok, y me gustó la cantidad de opciones que tiene, pero no puedo reproducir ningún tema (aclaro que tengo la versión con Gnome) Me sale un cartelito que me indica un error con el dispositivo de sonido, que a continuación les transcribo:

> Phonon: KDE´s multimedia library
The audio playback device HDA ATI SB (ALC268 Analog) does not work. Falling back to defaultQue opinan? Se puede solucionar? Espero que si, y como siempre gracias por su ayuda, saludos
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by WanderingKnight on 2009-06-16
Probá instalar el backend de xine (phonon-backend-xine), y configurá Amarok para que use ese backend (se puede hacer desde las opciones de playback).

Fijate y contanos.

---

### Post by Tenisfan on 2009-06-17
> **WanderingKnight said:**
> Probá instalar el backend de xine (phonon-backend-xine), y configurá Amarok para que use ese backend (se puede hacer desde las opciones de playback).

Fijate y contanos.

Aha, y como sería eso? Soy bastante nuevo en linux, y no tengo mucha idea al respecto. Gracias

EDIT: Lo instale a traves de sinaptic, busque el nombre del paquete y lo tildé. Ahora, en cuanto a las opciones de Amarok, no encuentro como poner para que use el bakend ese que me decis
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by dirty fingers on 2009-06-17
ummm como instalaste ? suena a que falta alguna dependencia. 

[SIZE=1]Pequeño comentario que no contribuye a tu pregunta pero esta relacionado.
Lo mejor por cuestión de rendimiento, compatibilidad, etc es usar aplicaciones para tu distribución. Hay muy buenos reproductores para GTK, proba Exaile y banshee por ejemplo.[/SIZE]

---

### Post by Tenisfan on 2009-06-18
> **dirty fingers said:**
> ummm como instalaste ? suena a que falta alguna dependencia. 

[SIZE=1]Pequeño comentario que no contribuye a tu pregunta pero esta relacionado.
Lo mejor por cuestión de rendimiento, compatibilidad, etc es usar aplicaciones para tu distribución. Hay muy buenos reproductores para GTK, proba Exaile y banshee por ejemplo.[/SIZE]

Al programa Amarok lo instale desde el menu de aplicaciones, con agregar y quitar...y despues y el bakend de xine, con synaptic, porq a la consola no la manejo bien. Seguramente falta algo, pero no se que será. Con respecto a tu sugerencia, tengo instalados exile y banshee, los 2 funcionan muy bien y los uso bastante, simplemente quería probar amarok, me pareció mas completo que los otros
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by WanderingKnight on 2009-06-18
Para configurar el backend:

Settings->Configure Amarok->Playback->Sound System Configuration->Backend

(perdón, tengo todo el sistema en inglés, así que no sé cómo es en español).

---

### Post by Tenisfan on 2009-06-19
> **WanderingKnight said:**
> Para configurar el backend:

Settings->Configure Amarok->Playback->Sound System Configuration->Backend

(perdón, tengo todo el sistema en inglés, así que no sé cómo es en español).

Hice lo que me dijiste, pero lamentablemente no me aparece la opción para configurar el backend, no se a q se debe. Pongo una captura de pantalla para que se vea lo q me aparece:
_[IMG]http://img269.imageshack.us/img269/996/configureamarok.png[/IMG]_

[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by WanderingKnight on 2009-06-20
Ah, perdón, yo estoy usando Amarok 2.1.1 que viene con la beta de KDE 4.3. Seguramente fue agregado en la 2.1 de Amarok.

Si querés probarlo, podés agregarte los [repos experimentales de KDE](https://launchpad.net/~kubuntu-ppa/+archive/experimental). Total como no usás KDE no creo que te haga mucho drama (a mí me andan bárbaro y uso Kubuntu).

---

### Post by guillermolisi on 2009-06-20
> **WanderingKnight said:**
> Ah, perdón, yo estoy usando Amarok 2.1.1 que viene con la beta de KDE 4.3. Seguramente fue agregado en la 2.1 de Amarok.

Si querés probarlo, podés agregarte los [repos experimentales de KDE]("https://launchpad.net/%7Ekubuntu-ppa/+archive/experimental"). Total como no usás KDE no creo que te haga mucho drama (a mí me andan bárbaro y uso Kubuntu).
No me parece una solucion al problema y menos si dijo que no es experimentado.

Se puede meter en mas problemas que en encontrar una solucion al que ya tiene, por impericia o lo que fuera.

Ademas, si usa Gnome, que la solucion venga por ese lado.

---

### Post by WanderingKnight on 2009-06-21
Bueno, bueno, pero siempre se puede aprender, no? :)

Lo dije porque justamente, como usa GNOME, es dificil que se le rompa todo. Yo tuve problemas al principio pero justamente porque transicione de KDE 4.2 a KDE 4.3, y cambiaron muchisimas cosas de Plasma. En este caso no creo que pase nada... y ademas aprender como agregar un repo no esta mal :)

---

### Post by guillermolisi on 2009-06-21
> **WanderingKnight said:**
> Bueno, bueno, pero siempre se puede aprender, no? :)

Lo dije porque justamente, como usa GNOME, es dificil que se le rompa todo. Yo tuve problemas al principio pero justamente porque transicione de KDE 4.2 a KDE 4.3, y cambiaron muchisimas cosas de Plasma. En este caso no creo que pase nada... y ademas aprender como agregar un repo no esta mal :)
Pero agregar un repo es OT para este thread a menos que sea parte de una solucion efectiva :D

---

### Post by Tenisfan on 2009-06-22
La verdad es que no quiero complicarla demasiado, actualmente tengo el sistema bastante estable y no se si lo voy a poder arreglar si empiezo a meterle mano. Bueno, de todos modos les agradezco a todos por tratar de darme una solución, si alguno se le ocurre otra cosa, espero su respuesta:D
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by wildemad on 2009-09-18
Yo tenía el mismo problema y lo solucioné con esto:

```
sudo apt-get install libxine1-ffmpeg
```

La versión que tengo del Amarok es 2.0.2

Suerte.

---

### Post by matias_tati on 2009-09-19
sudo apt-get install phonon-backend-xine libxine1-ffmpeg

Metiendo eso en consola lo arregle al toque

---

### Post by guillermolisi on 2009-09-19
> **matias_tati said:**
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg

Metiendo eso en consola lo arregle al toque
Phonon viene "de fabrica" con KDE, asi como PulseAudio con Gnome.

---

### Post by mottocross22 on 2009-09-21
Cambia el nombre de la carpeta .xine
$mv .xine/ .xine-bak/

reinicia el amarok y listo!

---

### Post by matias_tati on 2009-09-21
> **guillermolisi said:**
> Phonon viene "de fabrica" con KDE, asi como PulseAudio con Gnome.

Pero el tiene gnome o lei mal??

---

### Post by Diegocon13 on 2010-01-13
> **mottocross22 said:**
> Cambia el nombre de la carpeta .xine
$mv .xine/ .xine-bak/

reinicia el amarok y listo!

Gracias amigo, eso sirvió

---

### Post by Arian_Tux on 2010-01-14
que debo agregar??? sudo apt-get install backend??? xD

Por favor tambien estoy interesado en el tema.

Muchas gracias.

---

### Post by guillermolisi on 2010-01-14
> **Arian_Tux said:**
> que debo agregar??? sudo apt-get install backend??? xD

Por favor tambien estoy interesado en el tema.

Muchas gracias.
En el post #14 tenes en detalle lo que tenes que poner en consola para completar los paquetes necesarios para que funcione (por lo menos para el caso de Matias).

---

