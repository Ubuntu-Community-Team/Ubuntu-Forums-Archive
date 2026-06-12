---
title: "Network Manager y KVM"
date: 2008-12-24
forum: Software
---

### Post by z37a on 2008-12-24
Gente tengo un problmon con intrepid ibex, con hardy esto no me sucedia, peor migre a intrepid pro algunas cosas que queria y bueno aca viene el problema.

Al instalar KVM este sin instala sin problemas, peor no logro hacer andar el bridge, si sigo el tuto de ubuntu el network manager me borra el resolv.conf y no tengo dns, pero si el bridge andando, y con el network manager no logro crear un bridge. Alguna idea de como poder utilizar kvm con intrepid???

- Lo pude solucionar:

Primero saque de la lista de redes cableadas todas las redes, ahi quedo el manager sin administrar, luego agregue lo necesario en /etc/network/interfaces y en /etc/resolv.conf agregue pro arriba del comentario los dns(poniendo nameserver IP.DEL.DNS.X), reinicie la red y ya estaba andando, ahh y luego en el virt-manager elimine la coneccion pro defecto y cree una nueva y ya estaba, ya me dejo crear maquinas virtuales con red y demas!!!!

---

