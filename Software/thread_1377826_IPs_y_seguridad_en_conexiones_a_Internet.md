---
title: "IPs y seguridad en conexiones a Internet"
date: 2010-01-09
forum: Software
---

### Post by alojarteya on 2010-01-09
hola mmm alguna de mis dudas es que mi routeer tiene una ip del tipo 10.0.1.x ysegun lo que lei es que del tipo 192.168.0.xx se adquiere mas seguridad en funcin de entrada de intrusos, y no hablo de virus sino de persones de mal proceder. siendo que creo que seme estan metiendo en mis conexiones. el pasarme de ip me dara mas seguridad. gracias por responderme un abrazo

---

### Post by guillermolisi on 2010-01-10
> **alojarteya said:**
> hola mmm alguna de mis dudas es que mi routeer tiene una ip del tipo 10.0.1.x ysegun lo que lei es que del tipo 192.168.0.xx se adquiere mas seguridad en funcin de entrada de intrusos, y no hablo de virus sino de persones de mal proceder. siendo que creo que seme estan metiendo en mis conexiones. el pasarme de ip me dara mas seguridad. gracias por responderme un abrazo
Tecnicamente no hay diferencias entre usar un bloque de direcciones u otro. La seguridad no pasa por ese lado.

Ademas, son direcciones privadas, equivalentes desde el punto de vista de la seguridad, que no se ven desde Internet (normalmente) sino que se ven desde las PCs que forman la LAN interna.

Si queres mejorar la seguridad de tu LAN, revisa si tenes servicios activos, como web, smtp abierto, etc., ya que el firewall de Linux abre los puertos (escucha) al exterior a partir de ellos. Si no tenes servicios activos, no deberias tener intrusos en tu maquina (que no es lo mismo que intenten entrar).

---

### Post by juancarlospaco on 2010-01-10
No.

Instala [GUFW]("apt:/gufw")

---

