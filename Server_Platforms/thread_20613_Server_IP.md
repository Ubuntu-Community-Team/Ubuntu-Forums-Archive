---
title: "Server IP"
date: 2005-03-17
forum: Server Platforms
---

### Post by TekZonz on 2005-03-17
Hello,

I was looking around but was not able to find an answer to my simple (at least I hope) question.

What command will tell me the server IP on the only network it's connected. 

And secondly, how do I manually set IP/DNS on my ubuntu server?

Thank you in advance for your help,

TekZone

---

### Post by diebels on 2005-03-17
[QUOTE=TekZonz]
What command will tell me the server IP on the only network it's connected. [/QUOTE]
```
route -n
```
[QUOTE=TekZonz]And secondly, how do I manually set IP/DNS on my ubuntu server?[/QUOTE]
Hoary has a bunch of gnome-admin tools for this, don't remember how that was on warty. Anyway, you can set ip adress of network interfaces like a ethernet card, with ```
ifconfig
```. See ```
man ifconfig
``` for details. DNS is set up in /etc/resolv.conf with "nameserver $ipofnameserver" lines. To run your own DNS server, you install somehting like bind9.

---

### Post by Myles3 on 2005-03-17
[QUOTE=TekZonz]

And secondly, how do I manually set IP/DNS on my ubuntu server?

TekZone[/QUOTE]


Just use the gnome network manager located in computer -> sys confg -> networking

then in the network box go to Properties

That should do it

And if you want to see you ip use Network Tools located in App -> sys tools -> network tools

---

### Post by TekZonz on 2005-03-18
Thank your for your help, I shall check all this out.

@Myles3, this is going to pretty difficult since it's a "custom" install and does not have Gnome installed.

---

