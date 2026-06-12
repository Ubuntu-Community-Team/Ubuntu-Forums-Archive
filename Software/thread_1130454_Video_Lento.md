---
title: "Video Lento"
date: 2009-04-19
forum: Software
---

### Post by beatlina on 2009-04-19
Buenas Gente... desde que instalé Ubuntu hace ya más de un año, nunca pude ver correctamente ningún tipo de video... y la verdad es que quiero solucionar esto, aunque no se por donde empezar.
Puedo abrir los video pero la lentitud de la imagen es mucha y queda feo. Busqué por el foro pero no encontré nada. Espero instrucciones. Gracias.:(

Ah una preguntita mas estuve chusmenado el HardInfo y en la parte de memoria me dice
Memory	968MB (498MB used)
eso quiero decir que estoy desperdiciando la mitad de mi memoria?

Gracias de nuevo.

---

### Post by Hei Ku on 2009-04-19
Te fijaste que tengas todos los codecs instalados? 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Y si a videos te referis a esa pobre imitacion de stop-motion que tiene Youtube o sitios similares, eso es culpa de Flash. :p

---

### Post by beatlina on 2009-04-19
Hei Ku, tengo los extras toditos instalados, y no me refiero para nada a eso video, me refiero a todos todos todos un DVD por medio de la lectora, una peli que baje, un capítulo de lost de buena calidad, lo que sea.

Ya me ayudaste una vez y me fue muy bien.. espero que esta vez sea igual... porque quiero ver todas las pelis que tengo en lista...

---

### Post by Hei Ku on 2009-04-19
Que reproductor usas para ver los DVDs?

---

### Post by beatlina on 2009-04-19
Tengo Instalados VLC, Toten y Mplayer, como usar no uso ninguno porque como se ve lento... jj pero probé con esos y algunos más que no recuerdo.

---

### Post by Hei Ku on 2009-04-19
tenes una Via, cierto? Recuerdo que fue una lucha configurarla.
Seguis con la  8.04?

En cuanto a la memoria, si no la usa un programa, linux carga cosas que pueda llegar a necesitar. Si no es asi, la descarta en cuanto necesite el espacio. Pero muchas veces podes hacer un top y ver que la memoria en uso es casi el 100% (incluyendo este cache), pero tenes libre el 50%.  :D

---

### Post by beatlina on 2009-04-19
Estoy con la 8.10, y tenes muy buena memoria tengo un VIA.

---

### Post by beatlina on 2009-04-21
Ya nadie me va a ayudar?

---

### Post by Hei Ku on 2009-04-21
No tengo mucha experiencia con los reproductores de video en gnome, pero supongo que vlc es el mejor, y si ese tiene problemas, no se me ocurre mucho.

Consulta: cuanta memoria tenes libre al tratar de ver un DVD?

---

### Post by beatlina on 2009-04-21
> Consulta: cuanta memoria tenes libre al tratar de ver un DVD?

No se cómo hacer para saber eso...

---

### Post by c4d0rn4 on 2009-04-21
> **beatlina said:**
> Ah una preguntita mas estuve chusmenado el HardInfo y en la parte de memoria me dice
Memory	968MB (498MB used)
eso quiero decir que estoy desperdiciando la mitad de mi memoria?

Gracias de nuevo.

tiene un giga de ram (y parece que video compartida)
Ram no creo que sea el problema.

Probá con gmplayer

alt+f2 gmplayer

Luego click derecho sobre el video que abras y le das a preference.

Ve a la solapa Video, selecioná xv X11/Xv
y tildá abajo las casillas:
Enable doble buffering
Enable direct rendering
Enable frame dropping


Yo con eso en mi pc viejita le hago andár algunos mp4 de hd.


Más que de ram te preguntaría de cuanto es el procesador que tenés.

Pd. 498 used, quiere decir que tienes usado 498 y que el resto los tenés libres para ser usado si exigis más a la pc.

---

### Post by beatlina on 2009-04-23
Bien c4d0rn4 con esto reprodutor veo muy bien. Lo único es que no me deja seleccionar xv X11/Xv, con x11 le alcanza.... El único drama es que no lo puedo usar el pantalla completa, cuando opto por esta opción amplía la pantalla pero el video queda chiquito... ¿me podes ayudar con esto?

Gracias!

---

### Post by c4d0rn4 on 2009-04-23
> **beatlina said:**
> Bien c4d0rn4 con esto reprodutor veo muy bien. Lo único es que no me deja seleccionar xv X11/Xv, con x11 le alcanza.... El único drama es que no lo puedo usar el pantalla completa, cuando opto por esta opción amplía la pantalla pero el video queda chiquito... ¿me podes ayudar con esto?

Gracias!

Sinceramente en x11 sólo yo tampoco lo puedo agrandar.

En cambio si pudieras seleccionar el xv, que te recomendé, no tendrías ese problema. Sinceramente no se porque no te dejaría seleccionar esa opción =S.

Lo único que te puedo decir es que en vlc al igual que en gmplayer podés cambiar las preferencias de video. Por allí probando diferentes configuraciones conseguís algo que te sea útil.

De todas las configuraciones que tengo disponibles, la que te pasé es por lejos la que mejor me funciona. Y la verdad fue hecha a pulmón con ensayo y error xD.

---

