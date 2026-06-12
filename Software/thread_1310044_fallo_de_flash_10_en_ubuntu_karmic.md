---
title: "fallo de flash 10 en ubuntu karmic"
date: 2009-11-01
forum: Software
---

### Post by Brath-ga on 2009-11-01
Hola, queria informar y a la vez preguntar si a alguien le ocurre el siguiente fallo.

Con la nueva version de ubuntu (9.10) al instalar el flashplayer 10 funciona perfectamente en firefox.

Sin embargo en google chrome o opera por nombrar algunos no lo hace.
Se ve el video pero no deja manejar los controles de los videos embedidos.

Supongo que sera cosa del ubuntu 9.10 ya que el jaunty (9.04) no presenta ese problema (Comprobado).

Si alguien sabe la forma de informar a los desarrolladores agradeceria respuesta.

---

### Post by emiliano_raso on 2009-11-02
> **Brath-ga said:**
> Hola, queria informar y a la vez preguntar si a alguien le ocurre el siguiente fallo.

Con la nueva version de ubuntu (9.10) al instalar el flashplayer 10 funciona perfectamente en firefox.

Sin embargo en google chrome o opera por nombrar algunos no lo hace.
Se ve el video pero no deja manejar los controles de los videos embedidos.

Supongo que sera cosa del ubuntu 9.10 ya que el jaunty (9.04) no presenta ese problema (Comprobado).

Si alguien sabe la forma de informar a los desarrolladores agradeceria respuesta.

Me pasa lo mismo. En Firefox anda perfecto, pero en Opera y Chrome no.
Al principio pensaba que era problema de la version de Opera hecha para KK, pero en Chrome pasa lo mismo y es el mismo Chrome que tenia hace dos dias en JJ.
Asi que es problema de Ubuntu con todos los demas Web Browser menos Firefox.

Mas allá de eso, desde el dia en que salió hasta hoy no vi a nadie hacer ningun comentario al respecto, por lo cual pienso que somos pocos a quienes nos pasa, o nadie se dio cuenta.

Por las dudas comentame, que maquina tenes?
Yo tengo una notebook Acer Aspire 5710.

---

### Post by guillermolisi on 2009-11-02
Consulta sobre donde conseguir Chrome movida hacia [aqui]("http://ubuntuforums.org/showthread.php?t=1311764") porque era OT para este thread.

---

### Post by emiliano_raso on 2009-11-04
"Encontré" una "pseudo-solucion". Es tan mentiroso lo que voy a decir que no se si le puede servir a otro.

Me puse a jugar con la consola y empezé:
$ sudo apt-get update
$ sudo aptitude update
$ sudo apt-get upgrade
$ sudo aptitude safe-upgrade
$ sudo aptitude install -f

Cuando tiré ese ultimo comando, me pidió desinstalar un elemento de flash, lo cual me llamó la atención, asi que le puse YES.
Lo desinstaló y creo que ya no tenia flash, pero por las dudas probé y en Firefox si tenia.
Abrí Opera y Google-Chrome a ver si se habia MAGICAMENTE solucionado el problema, y para Opera se solucionó, pero para Google-Chrome sigue igual.

Es una cosa rarisima, peeeeeeeeeero, funcionó. Odio que pasen estas cosas porque siempre la segunda vez no pasa igual y el problema persiste.


EDIT: Peor de lo que pensaba. Para OPERA se solucionó parcialmente por lo visto:
- Al darle click sobre el icono de PLAY en el video de esta pagina no sucede nada: [http://www.muylinux.com/2009/10/31/¿que-so-arranca-mas-rapido/](http://www.muylinux.com/2009/10/31/¿que-so-arranca-mas-rapido/)
- Pero al darle click sobre el icono de PLAY en el video en la pagina de YouTube, si funciona. Incluso mover la barra de progreso.

---

### Post by N3RI on 2009-11-16
> **Brath-ga said:**
> Hola, queria informar y a la vez preguntar si a alguien le ocurre el siguiente fallo.

Con la nueva version de ubuntu (9.10) al instalar el flashplayer 10 funciona perfectamente en firefox.

Sin embargo en google chrome o opera por nombrar algunos no lo hace.
Se ve el video pero no deja manejar los controles de los videos embedidos.

Supongo que sera cosa del ubuntu 9.10 ya que el jaunty (9.04) no presenta ese problema (Comprobado).

Si alguien sabe la forma de informar a los desarrolladores agradeceria respuesta.

tengo el mismo problema, pero en firefox (en realidad, en shiretoko) 

a veces funciona bien, a veces en los vídeos embebidos no funciona, pero si los abro en youtube sí hace caso. A veces es sólo el control de play, y a veces tampoco me permite hacer pausa.

No probé si pasa lo mismo en chrome

---

### Post by josecuervo86 on 2009-11-16
Mismo problema aca, tanto en Firefox como en Chrome. Tengo que usar la barra espaciadora para manejar el play/pause

---

### Post by matias_tati on 2009-11-16
Tengo el mismo problema en Opera....en Firefox anda perfecto....

---

### Post by MiguelAy on 2009-11-23
Yo tenia el mismo problema y se solucionó de manera muy simple: 
en el navegador Opera >ayuda>comprobar nuevas versiones y descargando
la última me funcionó, aunque me dio algún problema que también se solucionó 
desistalando algo así como opera-start, creo

---

### Post by emiliano_raso on 2009-11-25
> **MiguelAy said:**
> Yo tenia el mismo problema y se solucionó de manera muy simple: 
en el navegador Opera >ayuda>comprobar nuevas versiones y descargando
la última me funcionó, aunque me dio algún problema que también se solucionó 
desistalando algo así como opera-start, creo

Podrias ser un poco mas explicito por favor?

Gracias... saludos...

---

### Post by dirty fingers on 2009-11-25
en ubuntu 9.10 64bit me funciona bien chromium 4.0.257 usando el flash player que se baja de [acá]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")

---

