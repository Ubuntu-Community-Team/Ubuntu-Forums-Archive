---
title: "Multirole server"
date: 2007-04-09
forum: Server Platforms
---

### Post by JoeLosco on 2007-04-09
I am starting to set up a personal server at home with an older computer I have lying around.  I was thinking about using the Ubuntu LAMP setup, however I was also thinking about using this as my gateway/firewall between my home network and the internet.  I was thinking that making the server being the gateway would make it easier to set up openVPN and other "public" features available.  

Can this be done with relative safety?  Or is it necessary for the firewall and other public devices to be physically separate with port forwarding enabled on the firewall?  

Thanks in advance

---

### Post by rsermilik on 2007-04-09
More services makes the server more vulnerable  to attacks.
I would use a dedicated firewall and best with a third leg for an DMZ network where the public accessible servers would be placed.
If you have an old computer you could use the take a look at [www.m0n0.ch/wall/](www.m0n0.ch/wall/)
Monowall also gives you access through pptp and ipsec.

---

### Post by JoeLosco on 2007-04-09
That's what I was afraid of.  Unfortunately I only have 1 spare computer around to work with.  Might have to use my old linksys router to act as the firewall infront of the public server.  Just have to figure out how to isolate the DMZ from the internal network then.  

I had looked into alot of firewall solutions including m0n0wall, ipcop, endian, and a few others that I can't remember anymore.  I just liked the flexibility of running the Ubuntu setup instead of the fixed setups of the "prepackaged" firewalls..  

Thanks

---

### Post by MrHorus on 2007-04-09
> **JoeLosco said:**
> 
Can this be done with relative safety?  Or is it necessary for the firewall and other public devices to be physically separate with port forwarding enabled on the firewall?  


Relative safety, yes.

Adding more services and opening more ports will clearly introduce more potential vulnerabilities but I run web, mail, SQL and SSH from the one server and it's not something that I lose any sleep over whatsoever.

Best thing to do IMO would be to write a custom script that sets up some iptables rule to only allow connections from specific IP addresses if possible and drop all others - that's what I do for services like Apache and MySQL.

---

