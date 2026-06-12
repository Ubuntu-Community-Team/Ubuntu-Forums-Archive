---
title: "Dell Poweredge 1950 with Broadcom NetXtreme II 5708 Gigabit Ethernet"
date: 2006-10-18
forum: Server Platforms
---

### Post by Avian00 on 2006-10-18
Hello,

Ubuntu Server (Dapper) does not seem to recognize the network adapter in my Dell PowerEdge 1950.  It is a Dual Embedded Broadcom NetXtreme II 5708 Gigabit Ethernet adapter (the one that comes standard with this server).  Has anybody else gotten this to work?  If so, can you share with me how?  If not, does anybody have any advice on getting it to work?

Thanks in advance!

Matt

---

### Post by HeLiS on 2006-10-20
I'm having the exact same problem. just tried to install it then on the 1950 and got the same error. does anyone know how to get around this.

cent os is poo

---

### Post by roysatx on 2006-10-21
Ditto here!  Any help appreciated!

---

### Post by rcgabriel on 2006-10-27
Did you find [this thread]("http://ubuntuforums.org/showthread.php?t=226114")?  It's on the Poweredge 2950, but specifically discusses the Broadcom GB ethernet issue and how to make it work.  Hope this helps.

---

### Post by paul.maddox on 2006-10-27
I've only got 1 PowerEdge 1950 but was able to install Ubuntu Server on it successfully.

The network card gave me a lot of grief though, until...

I realised that the eth's are picked up by the kernel the wrong way around!

eth0: Labelled on the server as interface 2
eth1: Labelled on the server as interface 1


Took me bloody ages trying to debug till I realised then slapped myself on the forehead for not thinking of it sooner!

---

### Post by GoJimbo on 2007-03-22
Forgive a networking newb.

Inside a college campus network I have installed 6.06 LTS on a PowerEdge 1950 with a static ip.  The machine responds to pings while inside the campus network but not http or ftp.

Now wondering if this is my problem, I didn't install the machine on the rack and did not  check the network cable.

Is there anything to be done in the bios or in /interfaces?

Thanks.

---

### Post by cyrano24100 on 2007-03-31
> **paul.maddox said:**
> I've only got 1 PowerEdge 1950 but was able to install Ubuntu Server on it successfully.

The network card gave me a lot of grief though, until...

I realised that the eth's are picked up by the kernel the wrong way around!

eth0: Labelled on the server as interface 2
eth1: Labelled on the server as interface 1


Took me bloody ages trying to debug till I realised then slapped myself on the forehead for not thinking of it sooner!

Gosh, I'm relatively new on ubuntu/linux -- does the above happen post-install or pre-install, and you modify the network interface file for this?

---

