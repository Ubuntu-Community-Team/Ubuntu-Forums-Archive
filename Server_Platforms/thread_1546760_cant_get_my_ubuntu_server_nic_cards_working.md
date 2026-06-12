---
title: "cant get my ubuntu server nic cards working"
date: 2010-08-05
forum: Server Platforms
---

### Post by bathacid on 2010-08-05
i had just went out and got some older blade servers and put ubuntu server on it and when i was installing it it asked if i wanted to set an ip because it didnt get a dhcp responce i said no then because i was going to do it later when i do a ifconfig now all i get is a lo interface but if i do sudo lspci i get 2 ethernet controllers and they show as follows
2:03.0 Ethernet controller: Broadcom corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
2:04.0 Ethernet controller: Broadcom Corporation NetXtreme Bcm57j02x Gigabit Ethernet (rev 02)
anyone have any ideas to get these two cards so i can assign an ip address
im sorta new to ubuntu so take it easy on me lol and ty in advance

---

### Post by FuturePilot on 2010-08-05
You'll have to configure them via /etc/network/interfaces

[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html")

---

### Post by Iowan on 2010-08-05
You didn't mention which server version you installed.  There's probably little difference, but [here]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") is the 10.4 Server Guide.

---

### Post by bathacid on 2010-08-05
ty so much iowan man i was able to figure it out with the link you gave me real life saver

---

