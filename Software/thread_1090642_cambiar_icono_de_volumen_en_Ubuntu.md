---
title: "cambiar icono de volumen en Ubuntu"
date: 2009-03-08
forum: Software
---

### Post by leonardo83 on 2009-03-08
Buenaaaaas, gente tengo una duda.
Estoy personalizando mi escritorio, uso gutsy Gibbon, y ya puse el formato de hora de otro color, coloque el applet para que el rythmbox se vea mejor, cambie el icono de Ubuntu por el de Tux, etc.
Peeeero lo que queria hacer es cambiar el clasico icono de volumen que aparece por defecto en el panel (ese del parlantito) por otro muy bueno que encontre, queria saber cmo se hace para cambiarlo, si hay alguna opcion desde el editor de configuracion, desde otro lugar o si no se lo puede cambiar :(

espero respuestas, saludos a todos !!
dejo screen de como se ve todo ahora (perdonene el tamaño pero aun no s eponer bien las fotos :P)

[IMG]http://img17.imageshack.us/img17/7656/pantallazor.png[/IMG]



**PD** : morbid angel que recital...brutal (desvirtue total pero estuvo muy bueno! ;) )

---

### Post by Air23 on 2009-03-08
Ese icono se encuentra en la carpeta "status" de los temas de iconos.

Tenes que ir a la carpeta de los iconos que estas usando (en /home/usuario/.icons). Ahi segun el tema vas a tener una carpeta que dice "scalable" o muchas de nombres "16x16", "22x22", etc. Dentro de estas vas a "status" y ahi estan los iconos que queres cambiar:

audio-volume-high.png
audio-volume-low.png
audio-volume-medium.png
audio-volume-muted.png

---

### Post by leonardo83 on 2009-03-09
> **Air23 said:**
> Ese icono se encuentra en la carpeta "status" de los temas de iconos.

Tenes que ir a la carpeta de los iconos que estas usando (en /home/usuario/.icons). Ahi segun el tema vas a tener una carpeta que dice "scalable" o muchas de nombres "16x16", "22x22", etc. Dentro de estas vas a "status" y ahi estan los iconos que queres cambiar:

audio-volume-high.png
audio-volume-low.png
audio-volume-medium.png
audio-volume-muted.png

muchas gracias man!
lo probe y anda bien, pero eso si, tengo que agrandar el tamamño del panel superior pero no hjay drama.
Muchas gracias! te pondria una medallita pero no se como hacerlo :P
Abrazo

PD: como pongo solved en el thread? alguien sabe?

---

### Post by Air23 on 2009-03-09
> **leonardo83 said:**
> muchas gracias man!
lo probe y anda bien, pero eso si, tengo que agrandar el tamamño del panel superior pero no hjay drama.
Muchas gracias! te pondria una medallita pero no se como hacerlo :P
Abrazo

PD: como pongo solved en el thread? alguien sabe?

No hay por que

Respecto a tener que agrandar el panel¿Que tema de iconos estas usando? ¿Tiene solo la carpeta "scalable" o muchas correspondientes a los distintos tamaños de iconos? Porque si es asi tendrias que reemplazar el icono que vos queres en todas las carpetas y con los tamaños correctos (16x16 en la carpeta 16x16, etc)

PD: lo de marcar como solver por ahora no se puede ([http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714))

---

### Post by leonardo83 on 2009-03-10
> **Air23 said:**
> No hay por que

Respecto a tener que agrandar el panel¿Que tema de iconos estas usando? ¿Tiene solo la carpeta "scalable" o muchas correspondientes a los distintos tamaños de iconos? Porque si es asi tendrias que reemplazar el icono que vos queres en todas las carpetas y con los tamaños correctos (16x16 en la carpeta 16x16, etc)

PD: lo de marcar como solver por ahora no se puede ([http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714))

gracias. Mira estoy usando los iconos que se llama OSX iconset, que son iconos de mac o algo asi, ya no recuerdo de donde los baje. Hay una sola carpeta que se llama escalable que no tiene esos iconos que vos me decis (low,high etc), lo que yo hice es a los icono s que queria renombrarlos de esa forma y ponerlos ahi, pero sigo viendo los que ya tenia a menos que agrande el panel porque son grandecitos jeje, ponele tiene que estar el panel con un tamañao de 40 para arriba, y no me gusta como queda, es demasiado panel :D.
Vos em decis que lo cambie en otro lugar o que ademas lo copie en toooodas las otras carpetas? no entendi eso. Ami no me aparecen carpetas como 16x16 o demas :(

dejo screen que no se si sirve: ahi entre en .icons, despues en mi tema que es OSX_iconset, donde tengo 3 cosas: carpeta scalable, carpeta development y index.theme(?), el screen es de lo que aparece dentro de scalable (parte izquierda) y lo que esta dentro de status (parte derecha) :confused: Gracias

[CENTER][IMG]http://img18.imageshack.us/img18/7656/pantallazor.png[/IMG][/CENTER]

---

### Post by EnriqueK on 2009-03-10
Ya que estás usando Gutsy, te recomiendo descargar "assogiate", con este programa vas a poder redefinir la asociación de íconos para  los diferentees tipos de archivos, por ejemplo podés poner un ícono para todos los .mp3 , otro para los .ogg y así con todos, con esto vas a tener un alto grado de personalización , desgraciadamente este programa no sirve para versiones posteriores a Gusty, a pesar de seguir figurando en repositorios.
Para editar el tamaño de los íconos podés usar el programa "kiconedit", con el vas a poder hacerle además algunos retoques para mejorar , etc.

---

### Post by sambita on 2009-03-10
@leonardo83: de dónde sacaste los íconos que aparecen en el escritorio? porque me re coparon y me los quiero conseguir

---

### Post by leonardo83 on 2009-03-11
> **sambita said:**
> @leonardo83: de dónde sacaste los íconos que aparecen en el escritorio? porque me re coparon y me los quiero conseguir

decime que iconos te interesaron, son una mezcla de varios lados. Avisame y te los puedo pasar no hay drama. Saludos!

---

### Post by sambita on 2009-03-12
> **leonardo83 said:**
> decime que iconos te interesaron, son una mezcla de varios lados. Avisame y te los puedo pasar no hay drama. Saludos!

Los íconos que tenés de carpetas, sobretodo los de "otra música", "incomplete" y "Facultad". Si podés pasarmelos te lo agradezco mucho, sino igual decime de que temas son y yo los busco por ahi, disculpa las molestias, saludos!

---

### Post by leonardo83 on 2009-03-13
> **sambita said:**
> Los íconos que tenés de carpetas, sobretodo los de "otra música", "incomplete" y "Facultad". Si podés pasarmelos te lo agradezco mucho, sino igual decime de que temas son y yo los busco por ahi, disculpa las molestias, saludos!

No hay drama, te los paso, no es molestia ;)
Si queres mandame tu mail por MP (porque no lo veo en tu perfil) y te lod mando a tu casilla, no puedo decirte como se llaman porque los renombre y como decia, son iconos variados de muuuuchso que baje por internet :P

Saludos!

---

