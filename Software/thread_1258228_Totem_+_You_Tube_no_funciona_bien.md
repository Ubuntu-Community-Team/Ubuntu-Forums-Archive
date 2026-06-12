---
title: "Totem + You Tube no funciona bien"
date: 2009-09-04
forum: Software
---

### Post by cimarrón argento on 2009-09-04
Es la primera vez que hago esto, perdonen si lo mande en cualquier lado.
Soy novato linuxero; instalé Ubuntu Jaunty pero tengo un problema con el reproductor Totem 2.26.1 que viene con un complemento para examinar vídeos en YouTube, lo habilité y casi que funciona, al menos busca los videos del tópico pedido pero no los reproduce (Ha ocurrido un error, No se pudo abrir la dirección; quizá no tiene permiso para abrir el archivo.) Si lo ejecuto desde una terminal como root (sudo totem) me sale esto cuando sale el mensaje de error (** Message: Error: "http://www.youtube.com/get_video?video_id=oxDZW4k8tCY&t=vjVQa1PpcFOmws5_Tnmi3T1kHtPsJaRcPqeSEfEYakM%253D&fmt=18": Not Found
gstsouphttpsrc.c(980): gst_soup_http_src_parse_status (): /GstPlayBin:play/GstSoupHTTPSrc:source:
404 Not Found) Las demas funciones del reproductor andan bien, y en you tube on line tampoco tengo problemas.
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by Cajuma on 2009-09-04
Hola :
Realmente no se cual es el problema del Totem,
pero yo en este momento, estoy viendo un video
de youtube (Solsbury Hill de Peter Gabriel) 
escribiéndote, bajando La discografía de Paco de
Lucia con Ktorrent y leyendo el diario, pero tengo
instalado VLC, proba de instalarlo y después me 
contas, a mi me gusta mas que el Totem.
Saludos. :D

---

### Post by cimarrón argento on 2009-09-07
Hola. gracias por contestar, instalé VLC pero no me di la suficiente maña como para configurarlo para streaming, y tampoco encontré nada específico en la red, te agradecería si me comentas como hacerlo. muchas gracias.

---

### Post by Cajuma on 2009-09-07
> **cimarrón argento said:**
> Hola. gracias por contestar, instalé VLC pero no me di la suficiente maña como para configurarlo para streaming, y tampoco encontré nada específico en la red, te agradecería si me comentas como hacerlo. muchas gracias.
Mil disculpas por no contestar antes, pero trabajo todo el día y en el laburo
no puedo forear mucho.
Fijate en opciones> añadir medios, yo me arme una carpeta con los links que quiero
reproducir, y cuando inicio VCL voy a los que quiero ver.
Si no te sirve contame como lo acostumbrar a hacer y vemos....
Saludos. :)

---

### Post by cimarrón argento on 2009-09-07
Disculpas totales porque parece que voy a seguir molestándote un tiempo... En el VLC que instalé (0.9.9a) no tengo ningun menú Opciones/Añadir Medios... Si tengo Medios/Abrir Red pero ahí pongo [www.youtube.com](www.youtube.com) y no anda (eso es pura improvisación). Ahora la pregunta es, hay que agregarle algún plugin y complemento a VLC para tener la opción de hacer streaming... no tengo idea, te recuerdo que estoy empezando con GNU y ya he salvado algunos obstáculos gracias a gente como vos que responde. Gracias nuevamente.

---

### Post by Cajuma on 2009-09-07
A mi me funciona, tenés router ? si es así, posiblemente
tengas que configurar el puerto, y si no, estamos en el horno.
¡¡ Algún Ubuntero viejo por ahí !!
Saludos. :)

---

### Post by Cajuma on 2009-09-08
Hola de nuevo, estoy ocupadísimo con el trabajo pero encontré algo
que te puede servir:

[http://www.videolan.org/.../streaming.../streaming-howto-en.html](http://www.videolan.org/.../streaming.../streaming-howto-en.html)
[]("http://ubuntuforums.org/www.videolan.org/.../streaming.../streaming-howto-en.html")[http://www.engadget.com/.../how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/.../how-to-stream-almost-anything-using-vlc/)
[http://ubuntu-tutorials.com/category/media/](http://ubuntu-tutorials.com/category/media/)

Están en ingles pero se entiende, espero te sirva.
Saludos. :)

---

### Post by cimarrón argento on 2009-09-10
Bueno, bueno, ya me voy despidiendo de mis ganas de tener youtube en un reproductor. Seguí los hilos y el primero me da error de página, el segundo hace lo que te comenté que ya había hecho yo y no anduvo (medio/abrir red/...) la única duda que me queda de esto es con que puerto tenés configurada la red youtube? probé varios y lo mismo....y el tercer hilo no me agregó mayor información práctica (seguí los hilos hasta videolan). Mi conclusión es acerca de un comentario tuyo, debe ser un tema de router, yo no tengo porque estoy colgado de la red pública gratuita gubernamental wifi, en san luis.

De todos modos Cajuma, te agradezco la buena predisposición. Hasta pronto, si ubuntu quiere, y una última pregunta ¿cómo doy por cerrado el asunto?

---

### Post by guillermolisi on 2009-09-10
> **cimarrón argento said:**
> Bueno, bueno, ya me voy despidiendo de mis ganas de tener youtube en un reproductor. Seguí los hilos y el primero me da error de página, el segundo hace lo que te comenté que ya había hecho yo y no anduvo (medio/abrir red/...) la única duda que me queda de esto es con que puerto tenés configurada la red youtube? probé varios y lo mismo....y el tercer hilo no me agregó mayor información práctica (seguí los hilos hasta videolan). Mi conclusión es acerca de un comentario tuyo, debe ser un tema de router, yo no tengo porque estoy colgado de la red pública gratuita gubernamental wifi, en san luis.
Por las dudas, averigua si en esa red publica hay algun filtro que hayan dispuesto para Youtube, ya que hay ciertos servicios que si no se los tiene con cierto nivel de control, terminan haciendo que todos los recursos disponibles sean insuficientes.

Es decir, lo que Cajuma comento sobre el router puede no ser en tu ambito sino del lado del data center que administra la red.

> **cimarrón argento said:**
> De todos modos Cajuma, te agradezco la buena predisposición. Hasta pronto, si ubuntu quiere, y una última pregunta ¿cómo doy por cerrado el asunto?
La politica para el subforo de Argentina es no cerrar los threads salvo que sea necesario para evitar algun descontrol y/o desvio. Este criterio es asi para permitir que alguien con un problema relacionado con un hilo ya abierto lo pueda aprovechar y agregar su inquietud o comentario, cuando quiera/haga falta.

Si el tema consultado no tuvo una solucion contundente, queda sin la etiqueta de [SOLVED], asi cada uno puede evaluar previamente las posibilidades de encontrar una posible solucion antes de ponerse a leer todo el hilo.

---

### Post by cimarrón argento on 2009-09-11
Hola Gullermolisi; como decía al principio on line no tengo problemas (bah, tengo uno pero nada que ver con esto), si es como vos decís, si hay un filtro debe ser para el servicio de streaming (pienso yo), pero voy a comunicarme con el servicion del data center a ver que me dicen. Gracias por sumarte.

---

