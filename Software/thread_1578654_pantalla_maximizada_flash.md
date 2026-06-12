---
title: "pantalla maximizada flash"
date: 2010-09-20
forum: Software
---

### Post by darkimedez on 2010-09-20
Hola

Les cuento que he probado de todo para solucionar el tema de maximizar los videos de flash en ubuntu 10.04, que cuando intento hacerlo se me pone la pantalla en blanco.

Espero ayuda :(

Saludos, Darío.

---

### Post by RafaelG on 2010-09-20
> **darkimedez said:**
> Hola

Les cuento que he probado de todo para solucionar el tema de maximizar los videos de flash en ubuntu 10.04, que cuando intento hacerlo se me pone la pantalla en blanco.

Espero ayuda :(

Saludos, Darío.


Darkimedez,

Podrias indicar que version de **Flash** tienes intalado, puedes escribir **about: plugins** (sin el espacio entre los dos puntos y la P) en la barra de direcciones en firefox y pegar aca lo que te arroja.

Ahora algo basico que podria estar pasando es que este configurado el Compiz para que no te deje abrir de modo Full Screen una manera muy facil de poder solucionar el inconveniente es ir a:** CompizConfig Settings Manager -> General Options - > sacar el Check en la opcion *Unredirect Fullscreen Windows* -> atras -> Cerrar Compizconfig**   y ojala sea eso!

Saludos!

---

### Post by themasterdark on 2010-09-22
Además por favor indicanos si tu sistema es de 32 o 64 bits.

si no sabes o no estas seguro ve a un terminal y ejecuta:

uname -a

si es de 64 bits te dira en la parte final de la linea de respuesta x86_64

si es de 32 i686 (o algo parecido)

Saludos =)

---

### Post by Revoltoso on 2010-09-30
Hola, soy un poco nuevo en ubuntu y nuevo en el foro.

respecto al tema a mi me paso lo mismo, fue un problema con la compatibilidad con mi tajeta de video ATI integrada.

Lo que hice fue investigar como sacar lo máximo de la tarjeta (hay varias soluciones en internet)... pero para el problema de la pantalla en blanco lo que hice fue desactivar la aceleración gráfica de flash. Eso lo hice haciendo clic con el botón derecho sobre la pantalla de youtube, pinche configuración y desactive la casilla que dice "activar aceleración de Hardware", reinicias el video y todo listo.

Lo otro que mejora la cosa es revisar en synaptic o en el centro de Software de ubuntu los reproductures de flash instalados... si tienes dos deja solo uno... yo tenia tanto el gnash como el adobe flash... me decidí por adobe aunque hay quienes dicen que gnash es mejor, ahi vez tu.

Saludos
R.

---

### Post by darkimedez on 2010-10-04
Gracias revoltoso por la ayuda. eso solucionó mi problema que llevaba por mucho tiempo molestándome.

---

