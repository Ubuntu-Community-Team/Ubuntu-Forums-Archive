---
title: "compartir internet con Ubuntu"
date: 2008-07-08
forum: Software
---

### Post by Hernán-Amaya on 2008-07-08
Hola ubunteros, les cuento que en mi familia pidieron internet por cable, el tema es que quieren compartir esa conexión y la impresora con otras dos máquinas, ahora viene el pero, no quieren comprar routers ni nada. Mi propuesta fue usar una de las pc que tiene HH para compartir la impresora y la internet. El esquema de la red es el siguiente:

PC1: HH con la impresora y la conexión a compartir
PC2: Window$ 
PC3: HH

las tres están en red mediante un wireless AP 

baje el paquete bridge-utils para hacer el puente entre la conexión a compartir y la red wireless pero no pude hacer mucho.

saben de algún buen tutorial o si alguno me puede tirar una punta para resolver esto.

desde ya muchas gracias por su tiempo!!

---

### Post by faktorqm on 2008-07-10
El asistente de firestarter te dejaba compartir internet si mal no recuerdo, sino a lo sumo tirá algún script de iptables (dentro de este mismo sub-foro hay varios) y con el tema de la impresora, la respuesta es samba, si los otros clientes usan win, si no quizá haya otra solución mejor. Salu2!!!

---

### Post by excaliburs on 2008-07-13
si pudieras routear el modem seria fantastico.....fijate si el modelo del modem tiene esa posibilidad.
si es asi...pan comido!!
saludos y suerte

---

### Post by marianom on 2008-07-13
Un día de estos deberíamos armar una charla en IRC sobre como configurar IPTables, creo que sería muy valioso.

---

### Post by Mauro22 on 2008-07-13
Marianom: Aca hay bastente info para iptables. Sencilla sobre todo y con ejemplos:

[http://es.wikipedia.org/wiki/Iptables](http://es.wikipedia.org/wiki/Iptables)

---

### Post by charlymx on 2011-09-15
Hola mi opinión es que es mas fácil comprar un router que últimamente están muy baratos compra uno en internet usado y listo. pero tampoco no dejes de intentarlo con iptables si lo logras pues seria muy bueno.
suerte con eso:D

---

