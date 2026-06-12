---
title: "Router con Ubuntu server"
date: 2009-12-12
forum: Software
---

### Post by z37a on 2009-12-12
Gente, alguno tiene algun enlace con alguna buena guia para armar un router utilizando ubuntu server?

Por que estube viendo un par de guias y la verdad que no me funciono casi ninguna, lo que quiero es que mi server trabaje como router tambien, para ello tiene 2 placas de red, configure la placa eth0 para dhcp(internet) y la placa eth1 con la ip de mi red, configure el iptables, pero no me forwardea.

---

### Post by z37a on 2009-12-12
Me autorespondo:

[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

Probe con esto y funciono de 10 con un ubuntu server 9.04

Agrego: Me falto aclarar que esto funciona bien, pero hay que agregar todo lo de iptables ANTES del exit 0 del archivo rc.local!!!

---

### Post by juancarlospaco on 2009-12-12
**Vyatta**

---

