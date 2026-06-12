---
title: "Problemas con los permisos"
date: 2009-03-21
forum: Software
---

### Post by ddirenzo on 2009-03-21
Antes que nada gente me presento, me llamo Diego y hace muy poco estoy en esto de Ubuntu.
Comence con este sistema, ya que contrate un servidor con sistema ubuntu, y en mi casa puse ubuntu en una maquina para ir aprendiendo, y no mandarme macanas en el servidor.
Al servidor accedo via putty o con el NX Client.
El problema que tengo es que no se porque se volvieron loco los permisos de usuario que tenia en el servidor, hasta hace dos dias podia instalar programas, ejecutar lo que quisiera, como si nada, de repente no me permite hacer casi nada cuando quiero instalar nuevas aplicaciones, hace como que las instala pero no las instala, por ejemplo no me permite cambiar las fecha, no me abre el gestor de paquetes synaptis, me marca que existen actualizaciones voy para que las instale y nada, cree un usuario nuevo y no me permite cambiar los permisos de ese nuevo usuario me dice operacion no permitida 13.
Por favor si alguien sabe como lo puedo solucionar muchisimas gracias.
Saludos

---

### Post by Hei Ku on 2009-03-21
en el ssh, pone esto:

cat /etc/group | grep admin

Eso te tira que usuarios son miembros del grupo. Deberia aparecer tu usuario.

La otra prueba es ver si estan en el grupo de sudoers. Es el archivo /etc/sudoers
No lo vas a poder ver si no tenes permisos. :D

sudo cat /etc/sudoers

Ahi deberia figurar el grupo admin

---

### Post by ddirenzo on 2009-03-21
> **Hei Ku said:**
> en el ssh, pone esto:

cat /etc/group | grep admin

Eso te tira que usuarios son miembros del grupo. Deberia aparecer tu usuario.

La otra prueba es ver si estan en el grupo de sudoers. Es el archivo /etc/sudoers
No lo vas a poder ver si no tenes permisos. :D

sudo cat /etc/sudoers

Ahi deberia figurar el grupo admin

Cuando pruebo lo primero me pone
lpadmin:X:108:
admin:X:114:admin
que significa?

Cuando pruebo lo segundo me pone
is mode 0640, should be 0440 y por lo que veo desde NX ese archivo pertenece al root :( y no tengo forma de hacerme root

---

### Post by Hei Ku on 2009-03-21
si tu usuario es admin, entonces significa que estas en el grupo de administradores del equipo.

El problema es que por alguna razon el archivo tiene mal los permisos, pero solo lo podes arreglar con permisos de root.

Salvo que tengas el password de root, o que puedas entrar en modo de recuperacion, no hay mucha forma de arreglarlo.

Que fue lo que tocaste antes de que te pasara esto?

---

### Post by ddirenzo on 2009-03-22
Antes de que pasara esto lo unico que hice fue crear un usuario, luego de eso empezaron los lios.
El tema es como vos decis busque busque por San Google, y la unica es tener la pass de root que no tengo ni idea cual es o entrar en modo recovery que la verdad no tengo ni idea como hacer con una maquina que nunca voy a tener acceso fisico.
Asi que querido amigo muchas gracias por todo y cuando este solucionado te digo como fue.
Saludos

---

