---
title: "Apache: dynamic ip with virtual hostname?"
date: 2008-10-03
forum: Server Platforms
---

### Post by thunderbirdje on 2008-10-03
Hi :-)

Is it possible to assign a hostname (only needs to be available in the same LAN network) to a computer with a dynamic ip given?

I do now the solution is in DynDNS-service, but I don't want my website to be worldwide available.

To be more exact:

1) being able to plug in my laptop on different networks (dynamic ip?)
2) being able to serve my electronic platform to the available students by using a easier accessible way than first looking up my own (dynamic) ip and giving them 4 groups of numbers :-)
3) giving them user friendly access: e.g. [http://thewebsite/](http://thewebsite/) instead of [http://192.168.123.11](http://192.168.123.11)

This because I'm always plugging in my laptop to a different network, with a different subnet mask, ip-range, etc :-) So I can't use a static ip (like most servers do...).

I do hope it isn't a silly question, I'm totally new to apache configuration. Is there a solutions for this?

Thanks a lot!

---

### Post by fatbastard spice on 2008-10-03
The simplest would be if you could get some configuration settings added to the DHCP server that's being used in the various networks. If so you could get the same IP address assigned each time and associate that IP address with a name your students could use.

Alternatively if they've got wireless and you don't need access to the other network resources you could carry a wireless access point with you and either set up your machine with some limited server functionality or start up a virtual server and have that running in the background to provide the server functionality.

---

### Post by thunderbirdje on 2008-10-05
So there isn't an easy solution I guess?

Getting configuration settings added to the DHCP server isn't an option because not all of the networks where I log on are ours. :( :-)

So the best solution is maybe dynds? Can I block in apache al WAN access to my laptop-server? Thus allow all LAN access?

---

### Post by thunderbirdje on 2008-10-05
So there isn't an easy solution I guess?

Getting configuration settings added to the DHCP server isn't an option because not all of the networks where I log on are ours. :( :-)

So the best solution is maybe dynds? Can I block in apache al WAN access to my laptop-server? Thus allow all LAN access?

---

### Post by thunderbirdje on 2008-10-14
Can't I use the hostname of my pc to access?

I tried it: feng/dokeos, doesn't work, what work is: 192.168.123.2/dokeos.

My hostname is feng, am I doing something wrong? Or just missing?

---

