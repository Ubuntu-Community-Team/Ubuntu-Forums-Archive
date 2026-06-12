---
title: "Consulta LTPS"
date: 2010-05-05
forum: Software
---

### Post by Bytesn+1 on 2010-05-05
Gente, buenas noches. Les comento un poco estoy haciendo un proyecto con LTSP para la escuela de lenguas. Estoy en periodo de pruebas pero hay algo que me tiene a mal traer por que no lo puedo resolver. 
Tengo un servidor chico todavía por que es todo lo que me dieron; P4 2.8 Ghz, 2 GB de memoria ram, 2 placas de red 10/100 y un disco de 500 GB y aproximadamente 7 clientes delgados son todos p2 de 500 Mgz y 256 de ram. Los tengo configurado el servidor para que los clientes usen OpenOffice, para poder navegar, hacer búsquedas en internet y ahora el "problema" ver vídeos en youtube, no tengo manera de configurarlo para que funcionen mas de 3 clientes al mismo tiempo, no se ve de manera fluida aunque se escucha perfecto.
Estuve haciendo unas búsquedas con google y había encontrado unos scripts para greasemonkey que no usaban flash y usaban un el plugin de mplayer o totem, pero por desgracia para mi dejo de funcionar. Trate de usar otras alternativas pero sin tener algún tipo de éxito.
La pregunta es si existe alguna alternativa que ustedes conozcan??? desde ya muchas gracias por adelantado.

Datos de interés

 Probé con Debian lenny, Ubuntu 7.10 y Edubuntu, actualmente estoy usando Debian lenny con xfce 4.

Saludos Bytes

---

### Post by alfplayer on 2010-05-05
Con esos terminales ver videos en YouTube se complica. Para los de "alta definición" puede ser imposible verlos sin cortes.

---

### Post by Bytesn+1 on 2010-05-06
alfplayer, hasta te doy la razón...pero no se si conoces los scritps de greasemonkey hace un tiempo habia encontrado uno que no usaba flash y se llama "youtube without flash" y andaba muy bien, pero por alguna razón dejo de funcionar. El tema es que tambien quiero que me recomienden algunos de ustedes que alternativas tengo a esto, los terminales son muy chicos o el server es chico? con un switch mejor se soluciona? tengo un 3com de 10/100. Bueno desde ya muchas gracias por responder, saludos

---

### Post by alfplayer on 2010-05-06
No me queda claro qué es lo que no funciona con más de tres clientes al mismo tiempo.

---

### Post by Bytesn+1 on 2010-05-06
alfplayer, videos en youtube. Lo explico en el primer post que con 3 clientes al mismo tiempo los videos de youtube no se ven de manera fluida, y hace un tiempo habia encontrado un scripts de greasemonkey que funcionaba muy bien. Saludos

---

### Post by alfplayer on 2010-05-06
Si el script de greasemonkey no funciona más (ni una versión actualizada), otra posibilidad para probar es usar youtube.com/html5 y Google Chrome, pero no todos los videos están disponibles con HTML5.

---

### Post by Bytesn+1 on 2010-06-03
Encontre una posible solucion para que no me mate el servidor, es usar nbd en lugar de nfs. La ventaja que tiene usar nfs es que no es necesario crear una imagen. Se usa directamente el sistema montado en /opt/ltsp/i386. Como desventaja, podemos decir que a mayor número de usuarios el sistema se pone lento y ni hablar de correr video o sonido. Si usamos nbd para servir el sistema a los terminales, la desventaja es que es necesario hacer una imagen comprimida (ltsp-update-image). La ventaja está en que a mayor número de usuarios el sistema no se hace más lento, si no que se mantiene igual. Pero asi mismo me da error cuando bootea un cliente, me dice que el kernel no es el correcto y he visto en muchas guias y ninguna en si explica nada y todas tienen casi el mismo formato. Alguien tiene un proyecto funcionando? o alguien puede darme una mano?. saludos

---

