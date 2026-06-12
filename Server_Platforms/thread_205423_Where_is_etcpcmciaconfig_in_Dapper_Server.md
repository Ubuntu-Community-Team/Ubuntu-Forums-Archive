---
title: "Where is /etc/pcmcia/config in Dapper Server?"
date: 2006-06-28
forum: Server Platforms
---

### Post by Avian00 on 2006-06-28
I'm trying to install Dapper Server on Laptop with a Linksys NP100 Network Everywhere PCMCIA ethernet card.  This card has a known issue with Debian/Ubuntu in that the wrong module is loaded.  Rather than loading the "axnet_cs" module, the OS loads the "pcnet_cs" module.

In the past, all I've had to do is change one string in the /etc/pcmcia/config file from "pcnet_cs" to "axnet_cs".  You can read more about this known issue here:

[http://cnycomputerservice.com/deblap.html](http://cnycomputerservice.com/deblap.html)

Well I'm up against a wall with Ubuntu 6.06 Server in that it seems this file doesn't exist!  It exists in the Desktop version but not the Server version.  How can this be?  Is there a different file I should be modifying?  Basically, I need to tell Ubuntu not to load the "pcnet_cs" module when that card is installed, but to load the "axnet_cs" driver instead.  If I can't do it by modifying the file I used to modify, where can I do this?

Thanks in advance for your help!

Matt

---

### Post by harisund on 2006-06-28
I am not really sure, but what you are looking for is somewhat along the lines of pcmcia-utils or something. Do some checking, sorry I have a desktop and no need for PCMCIA :(

---

