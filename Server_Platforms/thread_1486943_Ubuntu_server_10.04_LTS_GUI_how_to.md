---
title: "Ubuntu server 10.04 LTS GUI how to?"
date: 2010-05-18
forum: Server Platforms
---

### Post by fred2028 on 2010-05-18
Hi,
 
I just installed Ubuntu Server 10.04 and I'm trying to install a GUI for it. I have physical access to the server but the server has no Internet connection. However, it does have USB ports and a DVD drive. How would I get a GUI (GNOME?) and LAMP running on it without Internet? Thanks!

---

### Post by NullHead on 2010-05-18
For this usage, I would just install the desktop version of ubuntu and install LAMP on top of that. 

```
sudo tasksel install lamp-server
```

---

### Post by CharlesA on 2010-05-18
Since it doesn't have an internet connection, you would probably be better off trying to install the desktop version and go from there.

Either that or use [APTonCD]("http://aptoncd.sourceforge.net/")

---

### Post by fred2028 on 2010-05-18
> **CharlesA said:**
> Since it doesn't have an internet connection, you would probably be better off trying to install the desktop version and go from there.
 
Either that or use [APTonCD]("http://aptoncd.sourceforge.net/")
Thanks! Does APTonCD require another computer with Ubuntu, or can I do it from my Windows 7 laptop?
 
Thanks!

---

### Post by CharlesA on 2010-05-18
> **fred2028 said:**
> Thanks! Does APTonCD require another computer with Ubuntu, or can I do it from my Windows 7 laptop?
 
Thanks!

Judging from the [FAQ]("http://aptoncd.sourceforge.net/doc-faq.html"), it would need to be installed on a machine (or virtual machine) running Ubuntu.

Best bet would be to either install Virtualbox and run ubuntu in a VM, or boot off of a livecd and do it that way.

---

### Post by arrrghhh on 2010-05-18
Either way, you really should just install the -desktop version of Ubuntu if you want a GUI.  The whole point of the server OS is to have as little overhead as possible.  If you want to install a GUI, then this probably is not your goal ;)

---

### Post by CharlesA on 2010-05-18
> **arrrghhh said:**
> Either way, you really should just install the -desktop version of Ubuntu if you want a GUI.  The whole point of the server OS is to have as little overhead as possible.  If you want to install a GUI, then this probably is not your goal ;)

Agreed.

---

### Post by windependence on 2010-05-18
Wow! I have to say I'm impressed with you guys. You really understand the goal of the server product!

Carry on gentlemen.

-Tim

---

### Post by fred2028 on 2010-05-19
Thanks everyone, I'll install desktop instead :D

---

### Post by dragos2 on 2010-05-19
This is how you can do it: I run a variant of this into production in 8.04 (emulating Microsoft terminal services)

```

apt-get install gnome-core gdm ubuntu-artwork

```

---

### Post by kushvarma on 2010-08-30
See friend... there is a simple code to install Ubuntu-desktop

sudo apt-get install ubuntu-desktop 


but INTERNET IS MUST!!!!

---

### Post by arrrghhh on 2010-08-30
> **kushvarma said:**
> See friend... there is a simple code to install Ubuntu-desktop

sudo apt-get install ubuntu-desktop 


but INTERNET IS MUST!!!!

Please don't do this on a server install.  There's several reasons not to... one of them was the internet told me not to!

[Proof...](https://help.ubuntu.com/community/ServerGUI)

---

### Post by CharlesA on 2010-08-30
> **kushvarma said:**
> See friend... there is a simple code to install Ubuntu-desktop

sudo apt-get install ubuntu-desktop 


but INTERNET IS MUST!!!!

If you want a GUI on yer server, there are a ton better options then GNOME. If you want Gnome on it, then just install Ubuntu Desktop straight out.

> **arrrghhh said:**
> Please don't do this on a server install.  There's several reasons not to... one of them was the internet told me not to!

[Proof...](https://help.ubuntu.com/community/ServerGUI)

+1. You can always forward X over SSH for stuff that requires a GUI or use screen for CLI stuff.

---

### Post by =ChAoS= on 2010-08-30
I'm running lucid server x64 version on a remote server and i use freenx and the no machines client to view it. I have installed just terminal, gedit and synaptic but still do most things with putty from my wondows desktop.
 
Not having a desktop on it means it doesn't look pretty and is barebones but i like it that way and only installed a couple of things to help me.
 
Not having your "server" on the net is not gonna be easy but i find that using nx has helped me, a server and ubuntu noob of around 2 months, see whats going on and to help understand the file structures etc.
 
I have successfully installed lamp and a mail server etc and i'm still tweekin the system. I also have my forum running on it. Like i said being a noob, looking in on it has really helped me understand how it works.

---

### Post by X1R1 on 2010-08-30
X ssh tunneling rules the world, and +1 to install the desktop version if you want that kind of setup. Server version is tailored to have less security vulnerabilities, and a graphical environment running on the same machine is a big security risk, plus if you really use it as a server it would just consume resources when you are not using the graphical environment (ie you configure a samba server, then you only have to come back once in a while to create new shares or assign new permissions, but most of the time it will be running on the background)

---

