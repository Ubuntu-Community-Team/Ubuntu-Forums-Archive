---
title: "Problema con videos..."
date: 2009-11-07
forum: Software
---

### Post by .NicK_LoVe on 2009-11-07
Hola gente, se ven los videos con colores raros como colores frios, ya instale los restricted y toda la verdura pero no pasa nada.
Sera configuracion de la placa?

Saludos

---

### Post by wolterh on 2009-11-07
Mira, te recomiendo que visites este foro en vez, que es en español: [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/)

Seguramente allí obtendrás más respuestas.
Saludos.

---

### Post by luks911 on 2009-11-07
> **woli said:**
> Mira, te recomiendo que visites este foro en vez, que es en español: [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/)

Seguramente allí obtendrás más respuestas.
Saludos.
Este es el foro del Argentina LoCo Team, así que sí hablamos (escribimos) español ;-)
> **.NicK_LoVe said:**
> Hola gente, se ven los videos con colores raros como colores frios, ya instale los restricted y toda la verdura pero no pasa nada.
Sera configuracion de la placa?

Saludos

Empiezo con preguntas: ¿Qué versión de Ubuntu es? ¿Qué placa de video? ¿Qué reproductor probaste? ¿Con qué tipo de videos? Y si podés explicar un poco más lo de los "colores fríos", mejor, tal vez con una captura. :)

---

### Post by .NicK_LoVe on 2009-11-07
Detallemos, tenia 9.04 y me pase al 9.10, es una pavilion 6768se y probe con vlc, totem y mplayer y en todos pasa lo mismo.

Agrego captura.

[IMG]http://lh4.ggpht.com/_1MTpJUl94ws/SvXBMMNyNCI/AAAAAAAABdo/G99V8eAoDKU/Pantallazo.png[/IMG]

---

### Post by luks911 on 2009-11-07
¿Qué placa de video es?
Además se ve como movido, ¿no?

También podés probar ejecutando ```
gstreamer-properties
``` y en la pestaña video cambiar y el plugin de salida.

---

### Post by .NicK_LoVe on 2009-11-07
la placa es NVIDIA GeForce 8400M GS, entre en gstreamer-properties y cambie en default output de la pestaña video, el plug in detectar automaticamente por el x windows system sin xv y en el test se vio bien, en la opcion anterior se veia como el video. (aclaro que cuando puse test aparecio la captura de webcam)

---

### Post by luks911 on 2009-11-07
Si en la prueba se vio bien (en realidad debería mostrarte como una señal de ajuste haciendo click en el botón Test al lado de donde dice Pipeline), podés probar en Nvidia-settings las opciones para cambiar brillo, contraste y gamma, se me ocurre.

---

### Post by .NicK_LoVe on 2009-11-07
bueno entre a la configuracion de nvidia-settings y la verdad q no toque nada pero se soluciono el problema... q raro, pero no me quejo del resultado jajaj
muchas gracias x la ayuda.
Saludos !!!

---

