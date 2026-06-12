---
title: "&quot;Mensaje : el servidor no soporta nuestro protocolo&quot;"
date: 2009-12-08
forum: Software
---

### Post by gabriel315 on 2009-12-08
Hola, tengo instalado el pidgin 2.4.1. en mi pc desde hace un mes. Todo bien hasta que hace unos dias me marca este error "el servidor no soporta nuestro protocolo" y no puedo utilizar el programa ya que no aparece ninguno de mis contactos. Soy nuevo en UBuntu    ¿ Podrian ayudarme ? Gracias

---

### Post by guillermolisi on 2009-12-08
Danos algun detalle mas como por ejemplo a que servicio te queres conectar (MSN, Jabber/Gtalk, ICQ, etc.)

---

### Post by suelopoder on 2009-12-08
A mi me sucede lo mismo.

> Danos algun detalle mas como por ejemplo a que servicio te queres conectar (MSN, Jabber/Gtalk, ICQ, etc.)
Me estoy conectando a MSN

La conxión(fallida) no demora, es inmediata. La consola de debug imprime:
&#65279;(13:39:13) account: Connecting to account <my cuenta>
(13:39:13) connection: Connecting. gc = 0x84cecc8
(13:39:13) msn: new httpconn (0x858c030)
(13:39:13) dns: DNS query for 'messenger.hotmail.com' queued
(13:39:13) dns: Created new DNS child 12607, there are now 1 children.
(13:39:13) dns: Successfully sent DNS request to child 12607
(13:39:14) dns: Got response for 'messenger.hotmail.com'
(13:39:14) dnsquery: IP resolved for messenger.hotmail.com
(13:39:14) proxy: Attempting connection to 64.4.50.62
(13:39:14) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(13:39:14) proxy: Connection in progress
(13:39:14) proxy: Connected to messenger.hotmail.com:1863.
(13:39:14) msn: C: NS 000: VER 1 MSNP9 MSNP8 CVR0
(13:39:14) msn: S: NS 000: VER 1 MSNP8
(13:39:14) msn: C: NS 000: OUT
(13:39:14) account: Disconnecting account 0x81f5240
(13:39:14) connection: Disconnecting connection 0x84cecc8
(13:39:14) msn: destroy httpconn (0x858c030)
(13:39:14) jabber: jabber_actions: have pep: NO
(13:39:14) connection: Destroying connection 0x84cecc8

Tengo pidgin 2.4.1 y ubuntu 8.04.

---

### Post by suelopoder on 2009-12-08
Encontré esto:
[http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#Pidgin2.4.3andolderversions](http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#Pidgin2.4.3andolderversions)

Parece que el protocolo que usaba mi version vieja de pidgin ya quedó en desuso y el servidor ya no la soporta.

En la página de pidgin encontré esto:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

Así que seguí las instrucciones, apareció el update manager e instalé la nueva versión.

Messenger anda y depaso me actualicé el pidgin para mi ubuntu hardy :D

---

### Post by Mauro22 on 2009-12-08
MSNP8


Claro, esta trabajando con el protocolo 8 cuando van por el quince :S

---

### Post by guillermolisi on 2009-12-08
> **suelopoder said:**
> Encontré esto:
[http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#Pidgin2.4.3andolderversions](http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#Pidgin2.4.3andolderversions)

Parece que el protocolo que usaba mi version vieja de pidgin ya quedó en desuso y el servidor ya no la soporta.

En la página de pidgin encontré esto:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

Así que seguí las instrucciones, apareció el update manager e instalé la nueva versión.

Messenger anda y depaso me actualicé el pidgin para mi ubuntu hardy :D
Y con todo eso resolviste el problema del asunto ?

---

### Post by kornykyano on 2009-12-08
En Hardy se soluciona con PPA - [https://launchpad.net/~pidgin-developers/+archive/ppa]("https://launchpad.net/~pidgin-developers/+archive/ppa")

---

### Post by suelopoder on 2009-12-11
> **guillermolisi said:**
> Y con todo eso resolviste el problema del asunto ?
Si, ahora tengo la nueva versión.
¿Vos tuviste algún problema?

---

### Post by guillermolisi on 2009-12-11
> **suelopoder said:**
> Si, ahora tengo la nueva versión.
¿Vos tuviste algún problema?
No porque no uso Pidgin. Preguntaba para marcar el thread como SOLVED.

---

