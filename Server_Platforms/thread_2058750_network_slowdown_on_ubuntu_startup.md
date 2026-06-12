---
title: "network slowdown on ubuntu startup"
date: 2012-09-16
forum: Server Platforms
---

### Post by superbike on 2012-09-16
Recently I have been having a problem with my ubuntu server installation.
It is a torrent(transmission-daemon) and ftp(proftpd) server running on an old atom box with 2G ram. It also has a LAMP server running.
As soon as i start my server the whole network suffers a slowdown. i tested even by stopping both the transmission and proftp daemons but the problem persists **please help**.
:cry:
I have tried updating and all possible things. Even the connection on the box is hopelessly slow.

Thanx in anticipation

---

### Post by cariboo on 2012-09-17
Check the IP address, if you are using dhcp to set the server IP address, it may be getting the same address as another system on the network. To avoid that type of problem, I set static IP addresses on my servers, as I've run into the same problem a few times.

---

### Post by superbike on 2012-09-17
i have issued a static ip to the box on the dhcp server

---

