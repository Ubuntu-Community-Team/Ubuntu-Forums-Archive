---
title: "Zimbra, la novedad!"
date: 2009-02-18
forum: Software
---

### Post by zeroadrenaline on 2009-02-18
Buenas, estoy a la batalla de levantar un mailserver IMAP, habia pensado en exim4 + dovecot + squirrelmail para la interfaz webmail, la verdad, nada facil, exim es un hueso muy duro de roer, mas cuando en la net hay tanto tuto que mas que ayudar confunde, pero bueno, me llego el comentario de una suite llamada Zimbra, soportada en debian (que es lo que a mi me interesa) y en ubuntu, entre otras como RH, Suse... demas.

atacheo la web de zimbra [http://www.zimbra.com/](http://www.zimbra.com/)

Se la catalogo como el gmail de los mailservers, por su agilidad, facil configuracion, eh interfaz amigable, y bueno, mi intencion es testearla, lo que quisiera saber es si alguno ya la probó, que le parecio, y si es tan maravillosa como dicen.
Un abraso para todos, cuidence, PAZ!.

---

### Post by guillermolisi on 2009-02-18
> **zeroadrenaline said:**
> Buenas, estoy a la batalla de levantar un mailserver IMAP, habia pensado en exim4 + dovecot + squirrelmail para la interfaz webmail, la verdad, nada facil, exim es un hueso muy duro de roer, mas cuando en la net hay tanto tuto que mas que ayudar confunde, pero bueno, me llego el comentario de una suite llamada Zimbra, soportada en debian (que es lo que a mi me interesa) y en ubuntu, entre otras como RH, Suse... demas.

atacheo la web de zimbra [http://www.zimbra.com/](http://www.zimbra.com/)

Se la catalogo como el gmail de los mailservers, por su agilidad, facil configuracion, eh interfaz amigable, y bueno, mi intencion es testearla, lo que quisiera saber es si alguno ya la probó, que le parecio, y si es tan maravillosa como dicen.
Un abraso para todos, cuidence, PAZ!.
Zimbra comenzo hace varios años atras y tuvo mucho empuje cuando el proyecto fue comprado por Yahoo que logro, se me ocurre, lo que se ve hoy como producto terminado.

Hubo varios casos de adopcion y tambien varios que han vuelto a lo que tenian o lo reemplazaron por Horde.

Los comentarios que me llegaron de parte de quienes hicieron la experiencia fueron que requiere bastante recursos de maquina ya que parece estar muy apoyado en Java. Si el hardware no es suficiente, corre gomoso.

No se si te sirve como dato pero con Sismo hicimos la experiencia de migrar un MS Exchange a Courier, Postfix, Ldap y Horde con Amavis y Postgrey, como componentes mas destacados, y hace mas o menos mes y medio terminamos otro proyecto en el cual se reemplazo, en la misma instalacion, Courier por Dovecot y el Horde original por el nuevo que incluye tres interfaces web: Tradicional, Dinamica y Movil (celulares).

Esto entre otras tareas que permitieron mejorar el servicio prestado.

Seguramente habra otras personas que podran aportar sus experiencias en el tema y darte una opinion mas al respecto.

---

### Post by zeroadrenaline on 2009-02-18
Me mataste guillermo, jejejeje, yo estoy en el capitulo 0 del maunal del buen adminstrador de mailserver, recien hace unos dias empece a captar como viene la mano con el tema de los diferentes mta, diferencias entre imap y pop3, los problemas que trae que tu cliente no quiera garpar un aip fija, luchar con dyndns, zoneedit, y nic.ar.
Aca me pidieron que les monte un mailserver, y los tipos no tienen mucha idea, o al menos no mas que la que yo tengo, para que te imagines, cuando le pedi que me abrieran el puerto 22 en el router, y que pogan un user y pass de dyndns para yo poder hacer ssh para laburar el servidor, me putio el dueño diciendo que yo le queria robar sus clientes, y sus datos. Al final entendio que es algo necesario, no puedo estar llendo todos los dias a su negocio para trabajarle el servidor, pero bueno, anegdotas.
Si es por el hard, voy a descartar la idea del zimbra, porque no tengo una maquina muy potente para montar el server.
Seguire luchando con exim hasta que pueda al menos, enviar un correo.
Desde ya gracias.
PAZ!.

---

### Post by josecuervo86 on 2009-02-20
Yo lo probe, y asi como lo probe lo saque. Como dijo guillermo, consume muchos recursos y con 512 de ram y un par de aplicaciones abiertas aandaba muy lento. Por ahi si tenes una maquina con bastante ram talvez ande bien, pero no te la recomiendo para una pc que este corta de ram

---

### Post by z37a on 2009-02-22
Yo lo probe en un virtual con 512MB de RAM con un Ubuntu server solo corriendo zimbra y andubo de 10, si bien es pesado, esta muy bueno, ojo son gustos, a mi me gusto bastante.

---

### Post by sarrazol on 2009-06-04
La verdad que yo lo instale a un cliente en una VM con 4GB de RAM y 120GB de disco y actualmente tienen alrededor de 410 usuarios y estan mas contentos que con el anterior servidor de Exchange 2007.
Aclaro que es una simple observacion.

---

