---
title: "Ip fija en Debian"
date: 2009-04-16
forum: Software
---

### Post by ramiro_md on 2009-04-16
Gente nuevamente yo, disculpen que siga preguntando cosas de Debian jeje, pero las otras comunidades no me gustan, me siento más cómodo acá en ubuntu-ar :D.
La cuestión es que quiero configurar la ip fija en una pc que tengo con Debian y leyendo por google encontré bastante info, la cual utilicé pero no me sirvió de mucho.
Básicamente lo que decía en muchos blogs y wikis era modificar el archivo /etc/network/interfaces (aquí dejo como lo tenía "originalmente"):

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

Y así lo modifiqué:
> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

adress 192.168.1.70 # ip nueva ("fija")
netmask 255.255.255.0
gateway 192.168.1.1 # ip del router
nameserver 200.42.0.111 200.42.97.111 # DNS de flash 

EL tema es que cuando inento hacer ping, a google por ejemplo, con la nueva configuración me dice "unknown host www.google.com" e ifconfig solo me muestra lo.
Em qué le ando errando ? hay algun archivo que tenga que modifcar y no me haya enterado ?.
Desde ya mchas gracias.

---

### Post by Mauro22 on 2009-04-16
Adress no va con dos d, o sea Address ??


Google devuelve direccion para address como adress, pero si pones direccion te devuelve solo address..


Probá combiando eso...


Segun el ejemplo es asi:

```

# An example ethernet card setup: (broadcast and gateway are optional)
#
# auto eth0
# iface eth0 inet static
#     address 192.168.0.42
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#         gateway 192.168.0.1

```

---

### Post by ramiro_md on 2009-04-16
:O mira vos..después me fijo si lo excribí bieno  si solo lo puse mal aca en el post.
Por otro lado, broadcast y network de donde conseguis esa info ?.
Gracias

---

### Post by Mauro22 on 2009-04-16
Si te referis al ejemplo, lo saque de aca [0].

Si te referis a broadcast y getaway, son:

Broadcast, es la ultima direccion de la red

si tu direccion es  192.168.1.70 broadcast es 192.168.1.255 

Y getaway ya lo tenes, que es el ip del router!


:D


[0] [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by z37a on 2009-04-17
proba poniendo los nameservers en el archivo resolv y no en el interfaces!!!!

---

### Post by ramiro_md on 2009-04-17
GRacias MAuro ! al final era lo de address que estaba mal escirto (a veces hace falta que mire alguién más). Un saludo y gracias !.

---

### Post by Mauro22 on 2009-04-17
Joya Che!!


Suerte!

---

### Post by faktorqm on 2009-04-18
> **z37a said:**
> proba poniendo los nameservers en el archivo resolv y no en el interfaces!!!!

zeta quiso decir que podrias configurar tambien los DNS en el archivo /etc/resolv.conf y no en el interfaces. Para mi es lo mismo. Salu2!

---

