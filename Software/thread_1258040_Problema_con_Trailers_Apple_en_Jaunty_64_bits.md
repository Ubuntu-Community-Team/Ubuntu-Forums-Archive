---
title: "Problema con Trailers Apple en Jaunty 64 bits"
date: 2009-09-04
forum: Software
---

### Post by serwwweb on 2009-09-04
Hola, estoy teniendo problemas con los trailers de la pagina de apple, NO LOS PUEDO VER. Ya probe buscando en google y encontre algunas supuestas soluciones, tales como instalar los plugins para firefox de vlc y mplayer, los codecs w32, y hasta ideas como instalar quicktime, cosa que no probe y prefiero evitar.

Cuando doy click en algun trailer, ya sea standard o high definition o me dice que me falta "Decodificador text/html" y el video no carga (en standard) o directamente no pasa nada en high.

Estoy usando Firefox 3.0.13 y tengo el plugin de totem-mozilla instalado
Los Gstreamer estan instalados y actualizados
Y usando Ubuntu Jaunty 64 bits

Desde ya les agradezco su ayuda.

---

### Post by pablo.s on 2009-09-04
Ese problema sucede porque
la gente de Apple está bloqueando
ciertos "user-agents" y nosotros
hemos caído en la volteada.

---

### Post by serwwweb on 2009-09-06
Entonces por el momento no hay solucion verdad?

---

### Post by santiagoward2000 on 2009-09-08
> **pablo.s said:**
> Ese problema sucede porque
la gente de Apple está bloqueando
ciertos "user-agents" y nosotros
hemos caído en la volteada.

¿Por qué será que no nos bloquean para ver los ads? :-k
¿Se puede cambiar la user agent line para que se detecte como otro sistema? ¿O solo te cambia el cómo qué navegador te ven?
Saludos!

---

### Post by pablo.s on 2009-09-08
> **santiagoward2000 said:**
> ¿Por qué será que no nos bloquean para ver los ads? :-k

Porque la publicidad es un derecho
universal.

> **santiagoward2000 said:**
> ¿Se puede cambiar la user agent line para que se detecte como otro sistema? ¿O solo te cambia el cómo qué navegador te ven? Saludos!

En este caso en particular lo que
utilizan para el filtrado es la parte
del user agent que dice "GNU/Linux",
ya que no tenemos un plugin de
Quicktime, por ende no somos usuarios
de productos Apple, por consiguiente
no tenemos derecho a ver trailers.

También se habia dicho que era por un
problemita en GStreamer (por Totem)
pero con el plugin de Mplayer tampoco
muestra los trailers... y se cuelga.

---

### Post by santiagoward2000 on 2009-09-08
Me parece que el problema no viene por la parte que dice "GNU/Linux", sino por la parte que debiera decir "QuickTime". Se pueden ver los videos corriéndolos directamente desde MPlayer con la opción **-user-agent QuickTime/7.6.2**.
Entonces, una "solución" sería copiar la dirección del video, y abrirlo por MPlayer. Por ejemplo:
```
mplayer -user-agent QuickTime/7.6.2 http://movies.apple.com/movies/lionsgate/gamer/gamer-tlr2a_h.640.mov
```
Ahora lo único que habría que hacer sería cambiar el user-agent del gecko-mediaplayer para poder verlos dentro del browser, pero por lo que [leí]("http://code.google.com/p/gecko-mediaplayer/issues/detail?id=34") solo hay un hack en la versión SVN, y no te deja cambiarlo a vos en caso que a alguien más se le dé por bloquear al que no use X reproductor.
No sé si algún otro reproductor como el VLC o Totem (que es el que dijo serwwweb en el primer post que usaba) tengan alguna forma de hacer esto mismo.
Saludos!

---

### Post by pablo.s on 2009-09-08
Bueno, me equivoqué y lo 
admito. Muy buen hack el
que creaste!

---

### Post by santiagoward2000 on 2009-09-08
> **pablo.s said:**
> Bueno, me equivoqué y lo 
admito. Muy buen hack el
que creaste!

Bueno, gracias... pero yo no "creé" nada...

---

### Post by santiagoward2000 on 2009-09-09
Me interesó el tema, y encontré una solución un poco más cómoda. En lugar de copiar la dirección del video y abrirlo por MPlayer, se puede simplemente remplazar la user-agent line del browser por la de QuickTime. Algunos ya tienen la opción para modificarlo. Si usás Firefox, creo que se puede desde **about:config**. Sin embargo, la forma más simple es instalar el add-on [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59"), y agregar uno nuevo con la siguiente línea:
```
QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)
```
Entonces, cuando esté seleccionada dicha línea, se van a poder ver los vídeos desde el Firefox sin la necesidad de abrir un reproductor aparte. A mí me anda con el plugin **gecko-mediaplayer**, pero me imagino que tendría que andar con cualquier plugin (mozilla-totem, mozilla-plugin-vlc, etc) que tenga los codecs necesarios instalados.
Saludos!

---

### Post by serwwweb on 2009-09-16
Bueno, muchas gracias por las respuestas, ya lo he probado y funciona bien, asi que doy el tema por terminado.
Muchas gracias a todos.

---

### Post by eddietours on 2009-09-16
Muchas gracias:guitar:

---

### Post by leosr on 2009-09-21
> **santiagoward2000 said:**
> Me interesó el tema, y encontré una solución un poco más cómoda. En lugar de copiar la dirección del video y abrirlo por MPlayer, se puede simplemente remplazar la user-agent line del browser por la de QuickTime. Algunos ya tienen la opción para modificarlo. Si usás Firefox, creo que se puede desde **about:config**. Sin embargo, la forma más simple es instalar el add-on [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59"), y agregar uno nuevo con la siguiente línea:
```
QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)
```
Entonces, cuando esté seleccionada dicha línea, se van a poder ver los vídeos desde el Firefox sin la necesidad de abrir un reproductor aparte. A mí me anda con el plugin **gecko-mediaplayer**, pero me imagino que tendría que andar con cualquier plugin (mozilla-totem, mozilla-plugin-vlc, etc) que tenga los codecs necesarios instalados.
Saludos!
Hola.
Dónde tengo que poner esa línea?
Gracias!

---

### Post by santiagoward2000 on 2009-09-21
> **leosr said:**
> Hola.
Dónde tengo que poner esa línea?
Gracias!

Hola!
La línea va donde dice **User Agent**. En **Description** poné algo como QuickTime, para que sepas cuál es.
También podés agregar un botón a la barra de herramientas para cambiarlas rápido.
Saludos!

---

### Post by leosr on 2009-09-21
> **santiagoward2000 said:**
> Hola!
La línea va donde dice **User Agent**. En **Description** poné algo como QuickTime, para que sepas cuál es.
También podés agregar un botón a la barra de herramientas para cambiarlas rápido.
Saludos!

Y las otras las dejo en blanco?

Salu2

---

### Post by santiagoward2000 on 2009-09-21
> **leosr said:**
> Y las otras las dejo en blanco?

Salu2

Yo dejé el resto como estaban y me anduvo. Mientras bloqueen solo al reproductor de video no hace falta cambiarlos.
Saludos!

---

