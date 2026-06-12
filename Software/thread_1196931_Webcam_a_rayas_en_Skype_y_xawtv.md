---
title: "Webcam a rayas en Skype y xawtv"
date: 2009-06-25
forum: Software
---

### Post by Fernando Gonzalo Pellico on 2009-06-25
Hola, buenas tardes a todos. Les cuento a ver si me pueden ayudar a resolver este problema.

Tengo una webcam instalada, concretamente un eyetoy. Tengo instalados los drivers y funciona correctamente en cheese, pero en skype y en xawtv se va la imagen a través de unas rayas. Probé un comando que parecería resolver el problema en bastantes casos, con nigún éxito. El comando es este:

 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Si embrago en cheese, veo perfectamente la imagen.


Si voy a gstreamer-properties, en la pestaña de video, si selecciono v4l2 y le doy a prueba se ve perfecto y sin rayas, pero en v4l no se ve nada, por si ayuda. He probado un montón de cosas, pero no encuentro solución.

Como ya me habeis ayudado en este foro en alguna ocasión, solicito ayuda de nuevo, a ver si consigo resolver este misterio.

Muchas Gracias a todos.

---

### Post by SLA_leandrin on 2009-06-25
Hola Fernando, que pasa si probás con el siguiente comando;

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Suerte...

---

### Post by Fernando Gonzalo Pellico on 2009-06-25
Pues, desgraciadamente, sucede lo mismo. Además he instalado el programa wxCam y también funciona perfecto. Intuyo que el problema viene de v4l2, pero no sé que puede suceder. Funcionan bien unos programas y otros no.

---

### Post by Hei Ku on 2009-06-25
Hubo unos cambios en v4l que requiere que los programas se actualicen. Los que actualizaron andan bien, los otros no.
Podes probar con una version beta o CVS, a ver si ahi ya estan arreglados.

---

### Post by Fernando Gonzalo Pellico on 2009-06-25
Hei Ku, el problema es que lo que yo necesito es el Skype. Mi familia está en España y acabo de ser padre, todos quieren ver a mi beba por la camarita.Y el Skype hace ya tiempo que no se actualiza. Tengo que encontrar una solución.En fin, seguiré investigando.

---

### Post by Hei Ku on 2009-06-25
Probaste con Ekiga?

---

### Post by Fernando Gonzalo Pellico on 2009-06-26
Si, conozco y he usado no sólo ekiga sino otros clientes SIP. El tema es que llevo un año para que mis parientes se acostumbraran al Skype y empezar de nuevo, como que no. Además, ninguno utiliza linux y ekiga es un nombre que ni registran. Voy a probar con al amsn2, aunque esté en beta, a ver si funciona, porque el amsn normal tiene el mismo problema con el video. 

En fin, pensé que habría solución, pero ya veo que no.

Un saludo y gracias de todos modos.

---

### Post by Fernando Gonzalo Pellico on 2009-06-26
Al final lo solucioné rescatando otra webcam de peor calidad que tenía, pero que funciona bien con el Skype y con el aMsn, así que bueno, por ahora el tema lo tengo resuelto.

Gracias a todos.

---

### Post by mat86 on 2009-10-08
Hola a todos,

No se si será un poco tarde, pero acabo de conectar mi webcam eye toy namtay (la plateada) y tenía el mismo problema, con el cheese funcionaba perfectamente, pero con el ekiga se veía con líneas horizontales verdes, y me he dado cuenta que el problema era por la resolución, al cambiar la resolución en el ekiga a 640x480 ha pasado a funcionarme perfectamente.

Espero que os pueda servir de ayuda. Un saludo.

---

