---
title: "Grub 2 (tengo dos discos)"
date: 2010-12-11
forum: Software
---

### Post by Vero1 on 2010-12-11
Buenos días a todos,

Me vi en la necesidad de formatear el disco duro donde se encontraba Windows y reinstalarlo.

En otro disco tengo a Lucid.

Como era de esperar,Windows se apoderó del arranque. Traté de recuperar el Grub mediante el SGD 1, sin resultados positivos. Entonces usé el SGD 2 que lo único que me permite es arrancar Ubuntu pero no fija el Grub para un arranque dual.

Hice consultas en Google y en ubuntu-es pero me encuentro con informaciones cruzadas y confusas.

Les agradecería me ayuden con la forma mas simple que haya, para recuperar el arranque dual mediante Grub2.

Desde ya muchas gracias.

---

### Post by biale on 2010-12-11
Lo mas sencillo, fijate si desde Ubuntu arrancado, haciendo desde consola...

sudo update-grub

... regenera la entrada de grub para windows. Y ademas Windows arranca con "las letras" correctas.

---

### Post by Vero1 on 2010-12-12
Te agradezco la sugerencia pero no podía entrar a Ubuntu para nada.

De todas formas reinstalé Lucid y ya está.

saludos

---

### Post by guillermolisi on 2010-12-12
Digamos que la salida a partir de una reinstalacion no es lo que podria llamarse una solucion categorica.

Funciona pero no ayuda para aprender como proceder en otras circunstancias (por ejemplo en las que una nueva instalacion no sea aceptable/posible).

Por estas razones le quito la etiqueta de SOLVED.

---

### Post by Vero1 on 2010-12-12
En un todo de acuerdo, pero como llevaba dedicando a este asunto demasiado tiempo y paciencia, sin encontrar una respuesta satis-factoria en ningun lado, habiendo usado primero SGD1 y luego el 2, habiendo consultado en Google,probado algunos tips que no funcionaron, consultado en Ubuntu-es y Ubuntu-ar, pues opté por esa salida.

Gracias por tu atención.

---

### Post by biale on 2010-12-12
Muy de acuerdo con Guillermo. Incluso habías dicho que Ubuntu arrancaba:

> lo único que me permite es arrancar Ubuntu

O sea que lo unico que faltaba era arreglar el grub...

---

### Post by Cajuma on 2010-12-13
Recién vi este post, la forma de recuperar Grub2 es la siguiente:

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")

Yo lo recupere así despues de una fallida instalación de otra distro, espero les sirva.
Saludos.

---

