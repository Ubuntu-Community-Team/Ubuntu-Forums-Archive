---
title: "IPTABLES....MASQUERADE no funciona."
date: 2011-08-26
forum: Software
---

### Post by quedefantasma on 2011-08-26
Hola Amigos...Estoy teniendo un problema con NAT
[FONT=monospace]
[/FONT]-A POSTROUTING -s 100.100.100.0/24 -o eth1 -j MASQUERADE

Cuando voy a cualquier sitio, me muestra mi IP interna y no la de eth1 que es la asignada por mi ISP...

Ip_Forward esta habilitado....en /etc/sysctl.conf con net.ipv4.ip_forward=1 

Nunca me había pasado...A que podría deberse esto?

Gracias y Slds.

---

### Post by alfplayer on 2011-08-26
¿A qué sitio/s?

---

### Post by quedefantasma on 2011-08-26
> **alfplayer said:**
> ¿A qué sitio/s?
por ejemplo.... [http://www.speedtest.net/](http://www.speedtest.net/)

Este sitio anteriormente reflejaba mi IP publica...ahora (despues de actualizacion UBUNTU) solo refleja mi IP privada...

Creo que esto me esta generando también problemas en otros sitios...

---

### Post by alfplayer on 2011-08-26
¿Qué dirección aparece exactamente y dónde en speedtest.net?

---

### Post by quedefantasma on 2011-08-26
> **alfplayer said:**
> ¿Qué dirección aparece exactamente y dónde en speedtest.net?

Anteriormente speedtest.net veia mi IP publica (la del proxy) 190.190.xxx.xxx que es la que me asigna mi ISP y como resultado sabia que estaba en Argentina y realizaba el test de velocidad correctamente.

Actualmente ve mi IP privada (la de mi LAN) 100.100.100.xxx y me indica que estoy en algun lugar por africa...

---

### Post by quedefantasma on 2011-08-26
Mi proxy / firewal (Squid + Iptables) tiene 2 placas...

eth0 para la lan y eth1 para internet

eth0 tiene IP fija (de la lan) y eth1 tiene IP por DHCP del ISP (Puedo asignarle IP fija pero cuando por algun motivo me la cambian se me cae la navegacion de la LAN) por eso la dejo como DHCP.

Tengo redireccion en los clientes de eth0:80 para que vayan al squid... y masquerade en la interfaz saliente eth1

---

### Post by alfplayer on 2011-08-26
OK. El problema es que esa no puede ser una IP privada. Mirá esto: [http://es.wikipedia.org/wiki/Red_privada]("http://es.wikipedia.org/wiki/Red_privada")

Mejor usá 10.0.0.X que es la más simple de escribir dentro de las permitidas.

---

### Post by quedefantasma on 2011-08-26
> **alfplayer said:**
> OK. El problema es que esa no puede ser una IP privada. Mirá esto: [http://es.wikipedia.org/wiki/Red_privada](http://es.wikipedia.org/wiki/Red_privada)

Mejor usá 10.0.0.X que es la más simple de escribir dentro de las permitidas.

Ok, voy a cambiar las direcciones de la LAN eso puedo probarlo.

...lo raro es que hasta ahora siempre funciono bien asi...(hace años cuando se armo esta red, sin internet ya estaba asi...) y hasta esta ultima actualización eso no sucedía...

Igualmente, no comprendo porque ven mi IP privada...cuando igualmente deberían ver mi IP publica....

Gracias por tu ayuda.

---

### Post by alfplayer on 2011-08-26
> **quedefantasma said:**
> Igualmente, no comprendo porque ven mi IP privada...cuando igualmente deberían ver mi IP publica....

Puede existir otro problema.

---

### Post by quedefantasma on 2011-08-26
> **alfplayer said:**
> Puede existir otro problema.

Si, hay algo raro...cambie mi IP por otra e igualmente se ve hacia afuera.

Gracias por la ayuda... sigo buscando... si se te ocurre algo comentame por favor.

---

### Post by alfplayer on 2011-08-26
> **quedefantasma said:**
> Si, hay algo raro...cambie mi IP por otra e igualmente se ve hacia afuera.

¿Con qué IP y con qué máscara quedó?

---

### Post by alfplayer on 2011-08-26
Ah, probá con speedtest.net para entender, porque con otros sitios puede ser por otra razón.

También podría ser por la configuración de Squid.

---

### Post by mama21mama on 2011-08-27
vía terminal para ver ip publica.

```
curl ifconfig.me
```

proba con otros navegadores. para ir descartando.

---

