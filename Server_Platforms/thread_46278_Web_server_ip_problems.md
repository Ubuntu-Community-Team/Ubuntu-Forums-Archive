---
title: "Web server ip problems"
date: 2005-07-04
forum: Server Platforms
---

### Post by robojamie on 2005-07-04
Hey, 
I've got AOLServer running on my computer and everything is running smoothly, but I can only accsess it from localhost and 127.0.0.1 I've tried changing the hostname and address varibles in the configuration file, but this dosn't seem to effect the server even after restarting. Do I need to add more information to /etc/hosts? It currently contains only localhost 127.0.0.1 ubuntu.

---

### Post by miss tina on 2005-07-04
yes i think you sould i 've put my network adress and domain name and hostname to it for apache2
make allso sure your broadcasting at the same adress at port 80 (/etc/networkinterfaces i think it is)

---

### Post by robojamie on 2005-07-04
Could you eloborate on your confguration of apache? Even though I'm not using apache I think it might help

---

### Post by miss tina on 2005-07-04
Bestand: /etc/hosts

[COLOR=Olive]127.0.0.1 localhost.tina.servepics.com localhost ubuntu localhost.localdomain
192.168.0.104 ubuntu tina.servepics.com
# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/COLOR]

network:
[COLOR=Olive]
Bestand: /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
broadcast 192.168.0.104
gateway 192.168.0.1
[/COLOR]
and somewhere in apacheconf is
[COLOR=Olive]LISTEN 80[/COLOR]

---

### Post by LordHunter317 on 2005-07-04
Your /etc/hosts may matter, but I doubt it is the issue.  Sounds like your aolserver configuration is setup to listen only on port 80.  I've never set it up, so I would look for the offical documentation to figure out how to change what addresses it listes on.

---

