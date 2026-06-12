---
title: "Sin internet luego de actualizar a 9.10"
date: 2009-10-30
forum: Software
---

### Post by rubioo on 2009-10-30
Hola, esta mañana actualize a KK (por internet). Cuando termina, reinicio la PC y (entre varios problemas que tengo), cuando trato de conectarme a internet no puedo :S
Aclaro que no aparece ningun error y la placa de red la detecta.

Mi ISP es Speedy, tengo un router HUAWEI SmartAX MT880, placa de red Fast Ethernet Familia RTL8139 (Realtek), Ubuntu KK 64 bits y kernel 2.6.31-14 (tampoco funciona con el kernel 2.6.28-16).

Cualquier ayuda es mas que bienvenida.

 Gracias y saludos.

---

### Post by Fak89 on 2009-10-30
> **rubioo said:**
> Hola, esta mañana actualize a KK (por internet). Cuando termina, reinicio la PC y (entre varios problemas que tengo), cuando trato de conectarme a internet no puedo :S
Aclaro que no aparece ningun error y la placa de red la detecta.

Mi ISP es Speedy, tengo un router HUAWEI SmartAX MT880, placa de red Fast Ethernet Familia RTL8139 (Realtek), Ubuntu KK 64 bits y kernel 2.6.31-14 (tampoco funciona con el kernel 2.6.28-16).

Cualquier ayuda es mas que bienvenida.

 Gracias y saludos.

Yo tengo exactamente el mismo problema.. algunos cierres de programa inesperados, pero la conección a internet tampoco funciona. Para colmo no me acepta el password de root :S

A ver que te dicen

---

### Post by FB91 on 2009-10-30
A mi tampoco me andaba internet pero era porque estaba mal configurado... desde sistemas - preferencias - conexiones de red lo configuré de nuevo y ya estaba funcionando.

Capaz que tu problema sea distinto, pero por las dudas revisá la configuración

Salu2

---

### Post by rubioo on 2009-10-30
Si, ya me fije en la configuracion, pero esta como antes (cuando tenia internet). Igual ahora voy a hacer como decis vos, voy a configurar otra vez todo.

 Gracias por contestar :)

---

### Post by rubioo on 2009-10-30
Finalmente pude conectarme a internet.
Aunque lo hice usando **pppoeconf**
Si alguien tiene alguna idea de como me puedo conectar como lo hacia antes, se lo agradeceria :)

---

### Post by anarko on 2009-10-30
Ami el gestor de redes de KK ( cad avez toma mas consistencia el nombre :p ) me hace lo mismo no hay forma de que recuerde la contrasela, solucion pppoeconf.

---

### Post by josecuervo86 on 2009-10-30
+1000 a pppoeconf

---

### Post by rubioo on 2009-10-30
Pero yo antes no me conectaba con pppoeconf, porque no puedo conectarme como lo hacia antes (desde el icono del area de notificacion)? :(

---

### Post by Fak89 on 2009-10-30
Yo tambien pude conectarme con el pppoeconf.
Pero la verdad que pregunto lo mismo que pregunta rubioo..

---

