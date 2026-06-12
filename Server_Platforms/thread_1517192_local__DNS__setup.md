---
title: "local  DNS  setup"
date: 2010-06-24
forum: Server Platforms
---

### Post by kronicle on 2010-06-24
ive been trying to setup dns on my LAN with no success. i have ubuntu server with mysql+bind+apache and freeradius. i  provide wireless services to a community. the users are mainly laptops that connect to AP's and are authenticated by freeradius. i want to set dns so that when you type the domain name in a browser eg (mydomain.lan) you get sent to my webserver. ive tried various tutos but i dont know if they are for my secnario cos they dont work or they are not too straight forward, after configuring zones do i need to configure apache to respond to the domain name?
i need help here, anyone with experience setting up local dns or good tutos plz help.

---

### Post by koenn on 2010-06-25
here's a bind quick start : [http://users.telenet.be/mydotcom/howto/linuxsbs/dns1.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/dns1.htm)

you probably also want dhcp so you can tell the clients what DNS server to use.
So you might consider using dnsmasq, it's a combined dns+dhcp server and a lot simpler than bind

and yes, you'll need to tell apache what name it should listen to (lookup ServerName, ServerAlias in the apache reference manual). Although with a bit of luck, the default website will always work, so if you dump some html there, you're already set.

---

