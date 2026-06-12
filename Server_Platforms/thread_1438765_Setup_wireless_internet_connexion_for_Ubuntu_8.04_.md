---
title: "Setup wireless internet connexion for Ubuntu 8.04 LTS server"
date: 2010-03-25
forum: Server Platforms
---

### Post by KYR77 on 2010-03-25
Hello!
I have recently installed Ubuntu 8.04 LTS Server Edition, with no GUI. I can't connect to internet, and therefore I can't use commands like "apt-get update" I am very new to Ubuntu and Linux in general. I do not even know how to configure this server yet. I need my server to connect to Internet through my wireless card (I have no cable connexion for now). 
Any help or steps to make it work will be greatly appreciated! 
Thanks!

---

### Post by hessiess on 2010-03-25
> **KYR77 said:**
> Hello!
I have recently installed Ubuntu 8.04 LTS Server Edition, with no GUI. I can't connect to internet, and therefore I can't use commands like "apt-get update" I am very new to Ubuntu and Linux in general. I do not even know how to configure this server yet. I need my server to connect to Internet through my wireless card (I have no cable connexion for now). 
Any help or steps to make it work will be greatly appreciated! 
Thanks!

[This](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html) page shows how to connect to a wireless network from the command line. Though if you are serious about running a server it would be *much* better on a wired connection.

---

### Post by KYR77 on 2010-03-25
Thanks!
Eventually, I'll have the server connected by wire of course! But for now, I need to make it work wireless.

Now I tried this, but it does not work. When I do "ifconfig", in the server command shell, I get only a loopback interface. No eth0 or eth1, like I would have expected. So the server do not "see" my wireless card. (I think). How do you tell to a server "hey, look, there is my wireless card, and use it to go on Internet, so I can finally do a apt-get command!"? 

Thanks very much,

---

### Post by hessiess on 2010-03-25
What wireless card do you have? try googling for the card name plus ubuntu or linux.

---

### Post by KYR77 on 2010-03-25
Dell *Wireless* 1390  802.11g Mini [I]Card
Broadcom 4306 Chipset
[/I]

---

