---
title: "Connect My Server to the outside world"
date: 2008-12-12
forum: Server Platforms
---

### Post by The.Raptor on 2008-12-12
Hi. I have an old computer that I have set up as a server to learn some stuff. I want to be able to access it from outside my network, but am unsure how to do this. any help would be appreciated.

---

### Post by martien on 2008-12-12
> **The.Raptor said:**
> Hi. I have an old computer that I have set up as a server to learn some stuff. I want to be able to access it from outside my network, but am unsure how to do this. any help would be appreciated.
You must have a real ip address and all you need is to install openssh-server and other servers (such as web,ftp,etc. for your needs). If you are behind a router you have to point some ports from the local ip to the static ip address (this that your ISP gave you)

---

### Post by gpsmikey on 2008-12-12
You also need to read the AUP from your ISP to make sure it is OK to have a server (or at least what their policy is on it).  Some ISP's get quite nasty when they find someone running a server - others seem to ignore it unless it is attracting a lot of traffic.

mikey

---

### Post by The.Raptor on 2008-12-12
I have the router and the IP. I just need to forward the ports so that when I type in my IP, I get to my server's hosted pages.

My setup:


[OUTSIDE WORLD]<->[LINKSYS INTERNET PHONE ADAPTER]<->[DUMB ROUTER]<->[SERVER]

the dumb router has no config interface, so when I type 192.168.1 into my browser I get to the phone adapter.

What ports do I forward or what?

Also, they wont mind as I am only using it to test some stuff and learn. (read the AUP)

---

### Post by martien on 2008-12-12
> **The.Raptor said:**
> I have the router and the IP. I just need to forward the ports so that when I type in my IP, I get to my server's hosted pages.

My setup:


[OUTSIDE WORLD]<->[LINKSYS INTERNET PHONE ADAPTER]<->[DUMB ROUTER]<->[SERVER]

the dumb router has no config interface, so when I type 192.168.1 into my browser I get to the phone adapter.

What ports do I forward or what?

Also, they wont mind as I am only using it to test some stuff and learn. (read the AUP)
Well edit your "[dumb router]" configuration and change it to give adresses to 192.168.2... and so the both networks will be fine and you could access your "[dumb router]" and your "[LINKSYS INTERNET PHONE ADAPTER]" at the same time.

---

