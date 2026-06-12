---
title: "Configuración IMAP de GMail en Thunderbird 3"
date: 2009-11-11
forum: Software
---

### Post by leosr on 2009-11-11
Hola.
Configuré en Thunderbird 3 beta 4, 2 cuentas de GMail; el problema es que me está bajando todos los mails y me está dejando sin espacio el HD. Creí haber configurado bien que sólo quería que me baje los de los últimos 6 meses para ver "sin conexión" pero parece que no.
Entre las 2 cuentas lleva 11,4 GB en el HD.

Alguien sabe cómo hacer que no baje todo??

Si ya fue posteado disculpen, no tuve tiempo de revisar.

Gracias!

---

### Post by Mauro22 on 2009-11-11
En la parte de configuracion de Gmail tenes para elegir entre:

a) Bajar Todo

B) Bajar desde ahora en mas

[[IMG]http://img691.imageshack.us/img691/9051/pantallazoo.png[/IMG]](http://img691.imageshack.us/i/pantallazoo.png/)





:KS

---

### Post by leosr on 2009-11-11
> **Mauro22 said:**
> En la parte de configuracion de Gmail tenes para elegir entre:

a) Bajar Todo

B) Bajar desde ahora en mas

[[IMG]http://img691.imageshack.us/img691/9051/pantallazoo.png[/IMG]](http://img691.imageshack.us/i/pantallazoo.png/)





:KS
Lo que ahí me sugerís es la configuración de POP3, yo lo tengo configurado con IMAP.

Gracias de todos modos!

---

### Post by guillermolisi on 2009-11-11
> **leosr said:**
> Lo que ahí me sugerís es la configuración de POP3, yo lo tengo configurado con IMAP.

Gracias de todos modos!
Con IMAP4 no deberia bajarte nada, a lo sumo los ultimos encabezados.

Con TB 2 lo vengo usando desde siempre con IMAP4 y nunca tuve ese incoveniente, ni con Gmail ni con ningun otro mailserver que soporte ese protocolo.

---

### Post by leosr on 2009-11-11
En las capturas pueden ver el espacio utilizado en GMail por una de las cuentas y el espacio que me ocupa dicha cuenta en mi PC.

---

### Post by leosr on 2009-11-11
> **guillermolisi said:**
> Con IMAP4 no deberia bajarte nada, a lo sumo los ultimos encabezados.

Con TB 2 lo vengo usando desde siempre con IMAP4 y nunca tuve ese incoveniente, ni con Gmail ni con ningun otro mailserver que soporte ese protocolo.

Sí Guille, algo debo tener mal configurado.

---

### Post by guillermolisi on 2009-11-11
> **leosr said:**
> Sí Guille, algo debo tener mal configurado.
O algo no anda bien con esa version de TB, cosa que bien se podria verificar cruzando configuraciones entre TB2 y TB3 para cuentas con el mismo protocolo.

---

### Post by leosr on 2009-11-11
por lo pronto me parece que voy a probar borrando la cuenta que ocupa 11 gb y volviendo a configurarla. No voy a tocar nada que no sea lo que sugiere Google.

---

### Post by leosr on 2009-11-11
Borré todo, instalé TB 2 y me tira el siguiente error: "Account exceeded bandwidth limits. (Failure)", que también me salía antes en TB 3. Hoy empezó con ese error, antes no.

---

### Post by leosr on 2009-11-11
Aparentemente ese error quiere decir que mi cuenta se bloqueó durante 24 hs., no sé por qué causa.
[http://www.google.com/support/forum/p/Google+Apps/thread?tid=0ece6b37ff80c552&hl=en](http://www.google.com/support/forum/p/Google+Apps/thread?tid=0ece6b37ff80c552&hl=en) 
Está en inglés, pero por lo que entiendo no soy el único que tiene este problema y además parece que tiene que ver con Thunderbird.

---

### Post by pablo.s on 2009-11-11
> **leosr said:**
> Aparentemente ese error quiere decir que mi cuenta se bloqueó durante 24 hs., no sé por qué causa.

Superaste el ancho de banda 
permitido para esa cuenta.
Posiblemente por haber bajado
muchos datos en muy poco tiempo.
Es una medida que toma cualquier
proveedor serio en sospecha de que
la cuenta de correo esté siendo
utilizada para enviar spam. No es tu
caso, pero del lado del servidor no
analizan mucho.

---

### Post by leosr on 2009-11-12
El bloqueo de la cuenta es seguramente por lo que me dicen. Ahora configuré TB 2 y nuevamente TB 3 y parece que funciona correctamente, aparentemente mi error fue activar la opción "Mantener para esta cuenta en esta computadora", deba haber un error en TB 3 que hace que baje todo más de una vez, si no no se como bajó 11 gb cuando en realidad tengo menos de 1 en mi cuenta.

Otra cosa que noté en TB 3 es que en la sección "Copias y carpetas" hay que dejar las opciones por defecto de lo contrario baja todo. 

Gracias a todos.

Por ahora no lo marco como SOLVED, voy a probar un poco más de tiempo.

---

