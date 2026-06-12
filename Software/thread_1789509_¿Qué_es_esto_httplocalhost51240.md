---
title: "¿Qué es esto: http://localhost:51240?"
date: 2011-06-23
forum: Software
---

### Post by ppellet on 2011-06-23
Hola a todos

Acabo de actualizar firefox de 4.0.1 a 5.0 (uso ubuntu 10.10) y ahora, cada vez que inicio firefox, comenzó a aparecer una ventana que dice:[INDENT]*Usuario y contraseña son solicitados por [http://localhost:51240](http://localhost:51240). El sitio dice: "bookmarkable-user-auth"*
[/INDENT]Y no tengo idea de que se trata. He intentado poniendo los diferentes users y passwords que tengo, pero ninguna funciona.

Otro dato. Tenía instalado _Openerp_ y lo desintalé. Pero no sé si esto será parte del problema.

He buscado solución, pero no he dado con ella y no sé como eliminar esta ventana ni porque aparece.

¿Alguna ayuda por ahí...?

Agradecido de antemano, me despido ubunteramente.

ppellet

---

### Post by asterix77 on 2011-06-25
Hasta donde sé localhost hace referencia a tu propio equipo, y el N°51240 hace referencia a un puerto dentro de tu equipo.

Podrías usar un escaneador de puertos tal como nmap, y te mostrará los puertos abiertos en tu pc, y quien lo está usando.

*"bookmarkable-user-auth" *Al parecer (creo) que el nuevo firefox 5 está solicitando autorización para importar tus marcadores de tu antiguo firefox u otro navegador al nuevo.


Más respuesta no se me ocurre.


Saludos

---

### Post by ppellet on 2011-06-27
asterix77 muchas gracias, la primera parte de tu respuesta me hizo recordar algunas configuraciones que tuve que realizar cuando instalé openerp y, desde ahí, llegué al tema de las contraseñas (no me preguntes cómo se me ocurrió revisar eso ?).

la cuestión es que, dentro de: Preferencias de Firefox -> Seguridad -> Contraseñas guardadas , se abrió una ventana donde aparecieron todos los usuarios y contraseñas que he usado, allí estaban estos asuntos del * [http://localhost:51240]("http://localhost:51240/")* y* "bookmarkable-user-auth".* Los borré y ahora veré si vuelve a aparecer.

por el momento creo que funcionó, si no es así, vuelvo a poner un post aquí mismo.
gracias mil[I]
:)

[/I]

---

### Post by ppellet on 2011-06-29
> **ppellet said:**
> asterix77 muchas gracias, la primera parte de tu respuesta me hizo recordar algunas configuraciones que tuve que realizar cuando instalé openerp y, desde ahí, llegué al tema de las contraseñas (no me preguntes cómo se me ocurrió revisar eso ?).

la cuestión es que, dentro de: Preferencias de Firefox -> Seguridad -> Contraseñas guardadas , se abrió una ventana donde aparecieron todos los usuarios y contraseñas que he usado, allí estaban estos asuntos del * [http://localhost:51240]("http://localhost:51240/")* y* "bookmarkable-user-auth".* Los borré y ahora veré si vuelve a aparecer.

por el momento creo que funcionó, si no es así, vuelvo a poner un post aquí mismo.
gracias mil[I]
:)

[/I]

¡Mala cosa! volvió a aparecer lo mismo, pero con otro número para el localhost. Aparece de vez en cuando, de manera que, lo dejaré así no más.

Todo esto comenzó con la actualización de firefox desde 4 al 5, no &#347;e que podrá ser, pero ya me aburrí de tratar de eliminarlo.

Muchas gracias de todas maneras.

Un saludo a todos.

---

### Post by asterix77 on 2011-06-29
Pega el listado de lo que te arroje el comando 

$netstat -a


Con esto verás los puertos de tu pc y el estado en que están.

Después se podrían bloquear.


Saludos

---

### Post by ppellet on 2011-07-01
> **asterix77 said:**
> Pega el listado de lo que te arroje el comando 

$netstat -a


Con esto verás los puertos de tu pc y el estado en que están.

Después se podrían bloquear.


Saludos


asterix77

corrí el comando que me indicas, pero sale una tremenda cantidad de líneas, demasiadas diría yo.

¿las incluyo aquí o las envío por email?... (no sé interpretarlas).

saludos :confused:

---

### Post by asterix77 on 2011-07-01
OK


Entonces pega la salida del siguiente comando, este solo te mostrará los puertos abiertos
$sudo nmap -sT -O localhost


Saludos

---

### Post by ppellet on 2011-07-04
> **asterix77 said:**
> OK


Entonces pega la salida del siguiente comando, este solo te mostrará los puertos abiertos
$sudo nmap -sT -O localhost


Saludos

asterix77, aquí va lo solicitado:

laptop:~$ sudo nmap -sT -O localhost

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-07-04 21:27 CLT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000097s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 998 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
5432/tcp open  postgresql
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.19 - 2.6.31
Network Distance: 0 hops

OS detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 1.95 seconds

---

### Post by ppellet on 2011-07-14
¿Alguién me puede ayudar con esto?
No se interpretar estos datos, ni tomar acciones en consecuencia.

Muchas gracias de antemano.

---

