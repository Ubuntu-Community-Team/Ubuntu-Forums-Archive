---
title: "Problema con el cover art de Rhythmbox"
date: 2009-08-25
forum: Software
---

### Post by bichopro on 2009-08-25
Desde hace unas semanas mi reproductor ya no encuentra ni la mas común de las caratulas.
Alguna idea?
Al parecer el problema seria desde donde descarga las caratulas que seguramente cambiaron el API o algo asi ya que otros reproductores toman en el mismo pc y conexion

---

### Post by mexico on 2009-08-25
Yo también tengo el mismo problema. Ojalá y alguien pudiera dar alguna idea sobre este asunto.

---

### Post by Carlos C on 2009-08-25
Hola. Perdonen la pregunta, pero de dónde saca Rhythmbox sus caratulas? porque yo uso amarok 1.4, que descarga sus caratulas de amazon y me está pasando lo mismo.

---

### Post by mexico on 2009-08-26
Yo se que Rhythmbox descarga las carátulas de la página de Amazon.

Este problema también me lo presentó el Reproductor de música Exaile cuando lo instalé pensando que era problema del Rhythmbox.

El Reproductor de música Exaile también descarga las carátulas de la página de Amazon.

---

### Post by bichopro on 2009-08-26
OK,entonces podriamos confirmar que es un problema con la api de amazon.
Alguien tiene una cuenta para postear el bug? seria un gran aporte, sobre todo si es en Rhythmbox por ser el reproductor por defecto.
Ademas voy a buscar info para ver si se arregla con la version que venga con karmic koala.
Gracias por las respuestas...

PD: configuren el plugin de lyrics (letras) y marquen todas las opciones para que puedan bajar mas rapidamente, este aun funciona bien

---

### Post by fer493 on 2009-08-27
Estoy teniendo el mismo problema con Rhythmbox desde hace unas semanas. Alguna data?

---

### Post by nopersona on 2009-08-27
A veces en banshee me pasaba lo mismo (también no me reconoce ciertas caratulas si no se llaman "folder" o "cover"), para eso usaba [Album cover art]("http://www.unrealvoodoo.org/hiteck/projects/albumart/"). Es muy buen programa, ya que baja las caratulas de distintos sitios y las pone directamente en los directorios, además abre toda la colección de una vez. A ver si les sirve de algo. 

Ahora con Amarok no tengo ningúno de esos problemas :P

Saludos!

P.S.: En ubuntuforums hay un hilo sobre este programa, si llegasen a tener alguna duda.

---

### Post by mruiz on 2009-08-28
Cámbiense a Banshee ;-) No tengo este problema

Para ver qué esta pasando y arreglar el problema, sería bueno hacer debug de Rhythmbox.

TIP: ejecutar en una terminal "rhythmbox -d"


Saludos!

---

### Post by mexico on 2009-08-28
Revisando la página del [Album Cover Art Downloader]("http://www.unrealvoodoo.org/hiteck/projects/albumart/"), que menciona nopersona, encuentro esto en su página principal: "Note that due to the latest changes in Amazon's Product Advertising API, Album Cover Art Downloader is unable to download any images from Amazon for the time being."

Respondiendo a la pregunta de bichopro: "Alguien tiene una cuenta para postear el bug?" <--- desafortunadamente yo no tengo.


Saludos.

---

### Post by kamus on 2009-08-31
> **mexico said:**
> Revisando la página del [Album Cover Art Downloader]("http://www.unrealvoodoo.org/hiteck/projects/albumart/"), que menciona nopersona, encuentro esto en su página principal: "Note that due to the latest changes in Amazon's Product Advertising API, Album Cover Art Downloader is unable to download any images from Amazon for the time being."

Respondiendo a la pregunta de bichopro: "Alguien tiene una cuenta para postear el bug?" <--- desafortunadamente yo no tengo.


Saludos.

Tranquilos que este error ya fue [reportado aquí.]("http://bugzilla.gnome.org/show_bug.cgi?id=593163"):P

Salu2

---

### Post by mexico on 2009-09-02
> **kamus said:**
> Tranquilos que este error ya fue [reportado aquí.]("http://bugzilla.gnome.org/show_bug.cgi?id=593163"):P

Salu2


Muchas gracias por el dato.

Saludos.

---

### Post by fer493 on 2009-09-03
En definitiva el servicio no sirve más?

---

### Post by fer493 on 2009-09-12
¿¿??

---

### Post by mexico on 2009-09-15
> **fer493 said:**
> En definitiva el servicio no sirve más?

Como ya lo indicó el kamus en su respuesta, este problema ya fue reportado. [Aquí lo puedes checar]("http://bugzilla.gnome.org/show_bug.cgi?id=593163").
El estado actual de este problema es "RESOLVED NOTABUG" lo cual significa, en pocas palabras, que en realidad no es un error del programa y que está en espera de verificarse por los "RhythmBox Maintainers" a los cuales se les asignó.
Desafortunadamente este problema tiene una prioridad normal, ya que se trata de un problema que no afecta la funcionalidad del programa.

Así que no queda mas que esperar.


Saludos.

---

### Post by fer493 on 2009-09-15
Entendido, gracias.

---

### Post by Visente on 2009-09-16
Desde Amazon ya avisan del cambio de API: [aquí]("http://docs.amazonwebservices.com/AWSECommerceService/latest/DG/index.html?RequestAuthenticationArticle.html")

---

