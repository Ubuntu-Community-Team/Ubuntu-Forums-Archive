---
title: "Best terminal server software for Ubuntu?"
date: 2007-03-25
forum: Server Platforms
---

### Post by meheheh on 2007-03-25
Hi,

I currently have Ubuntu 6.06.1 Server Edition installed. I'm planning to install X and some terminal server software so multiple users can use it, and if it's successful I'll likely buy a new server. Does anybody have any recommendation? And I know about LTSP; it's not what I'm looking for as I want clients to connect via RDP or VNC... or can LTSP do that? Any help finding suitable software is appreciated.

---

### Post by depele on 2007-03-25
so you wan't to rdp multiple users at once on one computer?

I don't know if that is possible with all the GUI ****.

But it is possible to work simultaneous on the same machine using ssh. 

Once I have tried to forward the X through ssh and putty.
But I was never able to do so.

grtz..

---

### Post by jonathan.lees on 2007-03-25
Personally I would install the 6.06 LTS Desktop edition and use [Nomachine]("http://www.nomachine.com/") , you will need to install the Nomachine client software on your clients as it uses it's own remote access protocol, but it works better and quicker than VNC.

---

### Post by meheheh on 2007-03-25
Ok, it's just that the 300GB hard drive on my current server is almost full and I don't really feel like backing up everything..........

But thanks, NoMachine looks good. I was thinking of 2X ThinClientServer but I'll give NoMachine a try when I have some spare time. Also, it does look like NoMachine supports other protocols:>  Thanks to its outstanding compression performances, NX is able to deliver X, RDP and RFB remote sessions using the same client. This is achieved by translating "foreign" protocols into X-Window, the native protocol of NX.I'm not entirely sure if that applies to the free version though.

---

### Post by depele on 2007-03-26
And from windblowz to linux? because not all my computers are running linux? 

grtz...


some troubles... can somebody help please

```
sudo dpkg -i nxserver_2.1.0-22_i386.deb
Selecting previously deselected package nxserver.
(Reading database ... 132158 files and directories currently installed.)
Unpacking nxserver (from nxserver_2.1.0-22_i386.deb) ...
dpkg: dependency problems prevent configuration of nxserver:
 nxserver depends on nxnode (>= 2.1.0); however:
  Package nxnode is not installed.
dpkg: error processing nxserver (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxserver
depele@Kubuntu:~/downloads$[CODE]
```[/CODE]

---

### Post by meheheh on 2007-03-26
> **depele said:**
> And from windblowz to linux? because not all my computers are running linux? 

grtz...You mean accessing a Linux terminal server from Winblows?

Sure, NoMachine has client software for all 3 OSes and it appears to support RDP as well.

---

### Post by depele on 2007-03-26
indeed! 

I was able to fix it! and it is nice!

One thing could be better. the server screen size scaling.

but all the rest! ok...

grtz..

de_pele

---

