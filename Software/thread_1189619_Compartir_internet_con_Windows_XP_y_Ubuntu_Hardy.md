---
title: "Compartir internet con Windows XP y Ubuntu Hardy"
date: 2009-06-16
forum: Software
---

### Post by rodolfojavier1982 on 2009-06-16
Hola, antes que nada si ya hay un thread sobre esto pido mil disculpas, estuve buscando con el buscador del foro y no encontre algo parecido.

El tema es el siguiente.

Tengo dos PCs conectadas a un router ZyXEL P600- series, por medio de cables de red (posee wi-fi, pero no lo utilizo). Tengo conexion a internet Speedy Duo.

Lo que quiero hacer es poder usar internet en ambas computadoras a la vez, cuando sea necesario, ya que si yo me conecto con Ubuntu, mi hermano con Win XP no se puede conectar a internet, y viceversa. 
Soy muy novato en el tema de redes y mas en GNU/Linux.

Que es lo que podria hacer para poder utilizar en ambas maquinas internet al mismo tiempo?

Cualquier consejo me vendria bien.

Gracias por su tiempo....

---

### Post by gmunioz on 2009-06-17
Hola rod...:

Lo mas simple: comprar un router

Conectas el router desde su puerto wlan al modem

Conectas las pcs con cables directos (no cruzados)

a alguno de los cuatro puertos lan del modem

Desde una de las pcs, accedes a la página web de

configuración del router. (192.168.1.1) casi siempre

Sigues el wizard, y le incorporas usuario y contraseña

A partir de ese momento el router se encarga de conectarse

mediante el modem a internet, y a todas las pcs conectadas

a el, les provee internet y les configura las IP por dhcp.

---

### Post by staar on 2009-06-17
ese aparatejo se puede configurar como router (necesario para que haga lo que vos querés que haga) [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132") (el asistente es para Ventanas pero en ubuntu es igual)

saludos

---

### Post by guillermolisi on 2009-06-17
> **staar said:**
> ese aparatejo se puede configurar como router (necesario para que haga lo que vos querés que haga) [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132") (el asistente es para Ventanas pero en ubuntu es igual)

saludos
Pero con eso no alcanza. Falta explicarle como configurar las maquinas para que ambas lleguen al modem configurado como router.

Si habilitas el servicio DHCP (asignacion dinamica de IP) para las PCs de tu red, resolves una muy buena parte de la cuestion.

Una vez hecho esto hay que probar si ambas PCs pueden navegar sin problemas.

Avanza con esto y contanos como te resulto.

---

### Post by rodolfojavier1982 on 2009-06-19
Muchas gracias a todos los que respondieron, ultimamente ando con poco tiempo pero este finde voy a tratar de hacer lo que dicen, aunque confieso que me da un poco de miedo... 
Las redes nunca fueron lo mio.
Vere que sucede. 
De nuevo.
Gracias!!!

---

### Post by WanderingKnight on 2009-06-20
> 
Lo que quiero hacer es poder usar internet en ambas computadoras a la vez, cuando sea necesario, ya que si yo me conecto con Ubuntu, mi hermano con Win XP no se puede conectar a internet, y viceversa.

Fijate que el router no le esté asignando la misma IP interna a ambas máquinas. Generalmente podés entrar a la consola de configuración del router poniendo la IP del router en un navegador (192.168.1.1 por lo general).

---

### Post by guillermolisi on 2009-06-20
> **WanderingKnight said:**
> Fijate que el router no le esté asignando la misma IP interna a ambas máquinas. Generalmente podés entrar a la consola de configuración del router poniendo la IP del router en un navegador (192.168.1.1 por lo general).
Para que eso funcione la PC debe estar en la misma red que el modem. Para el caso 192.168.1.x donde x es un valor > 1 y la mascara de red 255.255.255.0

---

### Post by rodolfojavier1982 on 2009-06-20
Solucion inesperada!!!
Bueno, les comento que ya esta funcionando perfectamente.
Como?
No sé, mi hermano lo configuro antes de que yo lo tratara de hacer. :p
Me hubiese gustado solucionarlo yo, para asi de paso aprender un poco mas, aunque admito que me daba un poco de miedo ya que de redes se poco y nada.
Gracias a todos por responder!
Saludos.):P

---

