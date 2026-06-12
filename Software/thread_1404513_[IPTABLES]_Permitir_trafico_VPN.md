---
title: "[IPTABLES] Permitir trafico VPN"
date: 2010-02-11
forum: Software
---

### Post by z37a on 2010-02-11
Gente estoy desesperado buscando como crear una regla en el iptables para permitir que mi servidor permita a mis clientes pasar trafico mediante pptp, alguna idea?

---

### Post by z37a on 2010-05-12
Bien despues de un tiempo me autorespondo con la solucion a mi problem.

Al intentar conectar a VPNs PPTP etras de un router Ubuntu armado con iptables no me podia conectar. Luego d epruebas y viendo resultados de sniffers note que cuando el servidor es un server Windows me conecaba sin problemas, ahora al ser un Router VIGOR(que permiten VPNs pptp) no ograba conectar y quedaba a la espera de paquetes en respuesta. Esto no era pro la falta de ninguna regla, simplemente era la falta de 2 mosulos al kernel Linux, el ip_nat_pptp y el ip_conntrack_pptp.

Esto lo note buscando pro internet y emta buscar y me tope con la siguiente pagina:

[http://www.peremolto.net/2008/07/pptp-gre-y-vpn-multiples-con-firewalls_07.html](http://www.peremolto.net/2008/07/pptp-gre-y-vpn-multiples-con-firewalls_07.html)

Bueno espero que si alguno tenia el mismo problema con esto lo solucione!!!!

---

