---
title: "Intrepid: Pidgin (muy) inestable"
date: 2008-11-03
forum: Software
---

### Post by hictio on 2008-11-03
Hola,
Alguien tiene este problema tambien?
En lo que va del dia se colgo como 5 veces; no encontre un patron todavia, puede pasar con muchas ventanas de chat abiertas, o solo con una.
Lo unico que hasta ahora vi es que se cuelga, es decir, se cierran todas las ventanas, cuando envio un mensaje.

Ahora voy a ver en los logs si encuetro algo, pero queria saber si alguien le paso tambien.

Es con la version stock de Pidgin de Intrepid.

---

### Post by Mauro22 on 2008-11-03
Correlo desde la consola y fijate que error sale cuando falla.

---

### Post by hictio on 2008-11-03
Gracias, no lo puedo matar ahora (lo necesito por el trabajo), lo que estoy haciendo es ver los mensajes de debug en la ventanita de debug (doh!) lo unico que dudo que en el tipo de crash que vi en el dia de hoy, dicha ventana sobreviva...
Apenas pueda lo mato, y lo arranco con debug desde el terminal, a ver si aparece algo.

---

### Post by hictio on 2008-11-03
Con la ventana de debug abierta, no se colgo mas desde el ultimo post... Que cosa mas rara.

---

### Post by User21 on 2008-11-03
Yo también lo noto muy inestable, pero SOLO ME SUCEDE cuando abro alguna cuenta de M_S_ N
 ¬_¬

---

### Post by hictio on 2008-11-03
> **User21 said:**
> Yo también lo noto muy inestable, pero SOLO ME SUCEDE cuando abro alguna cuenta de M_S_ N
 ¬_¬

Buen punto.
Me olvide... Solo lo uso con MSN a Pidgin, sin contactos en ningun otro protocolo.

---

### Post by Marcos on 2008-11-04
A mi también me ha presentado problemas Pidgin, específicamente cuando abro un chat (conversación con muchas personas). En Hardy tenía la misma versión desde un repositorio PPA y no arrojó este problema (incluso funcionaba con mucha estabilidad).

---

### Post by hictio on 2008-11-04
Hoy en la manana lo abri dormido, y no del todo consciente, y sin arrancarlo en modo debug desde un terminal como sugirio Mauro22, igualmente, como a los 10 mins crasheo, a pesar de tener la ventana de debug abierta.
Lo volvi a ejecutar, esta vez con debug desde el terminal, hasta ahora no tuve problemas, espero atrapar algo si hace un crash en el terminal.

> 
A mi también me ha presentado problemas Pidgin, específicamente cuando abro un chat (conversación con muchas personas). En Hardy tenía la misma versión desde un repositorio PPA y no arrojó este problema (incluso funcionaba con mucha estabilidad).


En lo personal, no tuve problemas con los chats, ayer estuve en varios, sin problemas (tenia la ventana de debug habilitada)

---

### Post by hictio on 2008-11-06
Esto es lo que pude capturar:

```

12:36:56) proxy: Connected to 207.46.26.168:1863.
(12:36:56) msn: C: SB 007: USR 1 xxxxxxxx@hotmail.com 1500108792.1887153.184172168
(12:36:56) msn: S: SB 007: USR 1 OK xxxxxxx@hotmail.com xxxxxxxx%20xxxxxxx
(12:36:56) msn: C: SB 007: CAL 2 xxxxxxxx@xxxxxxx
(12:36:56) GThread: file /build/buildd/glib2.0-2.18.2/gthread/gthread-posix.c: line 385 (g_thread_join_posix_impl): error 'No such process' during 'pthread_join (*(pthread_t*)thread, &ignore)'
dns[5810]: Oops, father has gone, wait for me, wait...!

```

Hubo ocaciones en las que al hacer crash Pidgin, se llevo consigo el terminal desde donde lo habia arrancado con la opcion de '--debug'(????)

---

### Post by hictio on 2008-12-11
Bueno, me cansé... Instalé aMSN, voy a ver si con ese tengo un poco más de suerte.

---

### Post by sitiomatic on 2008-12-14
para la red msn, yo uso emesene que para mi es una maza, me parece mucho mejor que amsn.
Yo uso pidgin para la red google talk y lo que me pasa es que cada tanto  me desconecta, es decir, figuro conectado pero la gente me dice que desaparezco....colgar no se cuelga. (uso 8.10)

---

### Post by hictio on 2008-12-14
Gracias, yo solo uso MSN, fundamentalmente porque en el trabajo es lo que se usa, se convirtio en el standard de facto, por decirlo de alguna manera.
Si por mi fuese, no usaria ningun IM :D
Con el aMSN no tuve crashes hasta el momento, pero la interfaz es... No se, "gigante", todo es grande, parece que el disenador grafico que lo hizo fuera un poco chicato.

---

