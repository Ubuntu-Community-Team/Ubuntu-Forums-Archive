---
title: "Sin sonido desde el upgrade a Karmic"
date: 2009-10-31
forum: Software
---

### Post by autusgo on 2009-10-31
Hola a todos,
Había encontrado otro thread para postear esto y de hecho los postié, pero como estaba en SOLVED no creo que nadie lo vaya a leer, así que acá voy de nuevo.

Hice el upgrade a Karmic Koala y desde entonces estoy sin sonido. En realidad me di cuenta que algunos programa emiten sonido pero **muy** bajo, otros ni siquiera eso.

Cuando prendo la PC me aparece una ventana que dice que KDE detectó un cambio en el hardware y que la placa de sonido que estaba ya no está, y me pregunta si la quiero desinstalar, a lo que respondo siempre que no.

Fui a System Settings -> Multimedia y en la parte de Audio Output veo 4 cosas:

HDA NVidia (ALC883 Analog)
HDA NVidia (ALC88 Digital)
[COLOR=Gray]HDA NVIdia, AL889 Digital (IEC958 (S/PDIF) Digital Audio Output[/COLOR]
PulseAudio

En ese orden. Estoy casi seguro que yo antes usaba la tercera (que ahora está en gris).

¿Alguien tiene alguna idea?
¿No hay alguna forma de que el sistema vuelva a escanear el hardware e instale la placa como hizo cuando instalé Kubuntu?

Gracias!

---

### Post by Mauro22 on 2009-10-31
Ahora no tenes sonido? o esta muy bajo??

---

### Post by autusgo on 2009-11-01
En alguno programas no tengo sonido, y en otros hay un sonido muy bajito.
Ej1. Amarok se escucha muy bajito; si subo el volumen al mango se escucha apenas.
Ej2. Audacious ni siquiera intenta empezar el tema, ponés play y no pasa **nada**.
Ej3. Youtube no tiene sonido, ni bajo ni nada. Los videos andan, pero no tienen sonido. (Ahora intenté volver a fijarme esto para estar seguro y ya no me andan ni los videos... ¬¬ Igualmente esto ya es parte de otro problema que solucionaré de alguna otra forma).

Por favor, alguien que me de una mano, no tengo ganas de estar swtcheando a Windows para poder escuchar música o ver un video.

Gracias!

---

### Post by josecuervo86 on 2009-11-01
Probaste con:

```
alsamixer
``` desde una terminal? Fijate si los canales no estan muy bajos

---

### Post by Mauro22 on 2009-11-01
Antes leí que alsamixer no viene en karmic. Así que si al hacer el comando anterior da error, instalalo desde synaptic

---

### Post by josecuervo86 on 2009-11-01
> **Mauro22 said:**
> Antes leí que alsamixer no viene en karmic. Así que si al hacer el comando anterior da error, instalalo desde synaptic

Cierto que sacaron el mixer!! Perdon por la errata

---

### Post by autusgo on 2009-11-01
Probé con el mixer del system tray. Igualmente probé con la consola y salió esto:

[I]alsamixer: function snd_ctl_open failed for default: No such file or directory
[/I]
Me fijé en KPackageKit y aparece como ya instalado, así que no sé porqué tira error.

Igualmente no creo que sea una cuestión de los canales bajos porque me tira el error de hardware que les dije cuando enciendo la máquina.

---

### Post by moreback on 2009-11-01
No sé como será en KDE, pero los usuarios de Gnome tenemos disponible las opciones que hay en Sistema -> Preferencias -> Control de volumen

Y en System Settings -> Multimedia (que debiera ser Sistema -> Preferencias -> Selector de sistemas multimedia) se deja con PulseAudio, ya que es éste el que se encarga de mezclar los sonidos de todas las aplicaciones.

Saludos.

---

### Post by autusgo on 2009-11-01
Bien, finalmente puse que **sí **a quitar la placa que estaba en gris, así que ya no aparece. y puse PulseAudio arriba en la lista de dispositivos, así quedó como preferida. Pero sigo sin audio.

En KDE para el control de volumen siempre voy al system tray y clickeo el parlantito.

---

### Post by guillermolisi on 2009-11-01
Dale una leida a [este post]("http://ubuntuforums.org/showpost.php?p=8215998&postcount=11")

---

### Post by autusgo on 2009-11-02
Ya lo vi, pero habla de Gnome. En una parte dice:
> [COLOR=BLUE]**Note 4: Kubuntu users:** Don't follow this guide - PulseAudio isn't used in your distribution.[/COLOR]

Me parece que, aunque no quería, voy a formatear y reinstalar. Voy a esperar unos días a ver si surge una idea copada o me ilumino.

Saludos!

---

### Post by guillermolisi on 2009-11-02
> **autusgo said:**
> Ya lo vi, pero habla de Gnome. En una parte dice:


Me parece que, aunque no quería, voy a formatear y reinstalar. Voy a esperar unos días a ver si surge una idea copada o me ilumino.

Saludos!
Upsss .. my fault. Me olvide de ese detalle.

---

### Post by Tosh78 on 2009-11-02
Antes de formatear fijate con Kmix (o kmixer). 
Yo en la version anterior tuve un problema parecido y lo solucione instalando esto y subiendo todas las barras de sonido.

---

### Post by autusgo on 2009-11-14
Miré todo lo que había que mirar del Kmixer, pero nada...
Reinstalé y voilá!

---

