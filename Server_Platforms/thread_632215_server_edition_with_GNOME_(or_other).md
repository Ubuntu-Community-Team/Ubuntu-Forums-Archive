---
title: "server edition with GNOME (or other)?"
date: 2007-12-05
forum: Server Platforms
---

### Post by var on 2007-12-05
hi all,

I'm planning to install the server edition of Ubuntu 7.10. I'm moving first steps about server configuration and management and so I think that the presence of a visual environment will make my life easier. so, the question: is acceptable (from the security, performance and other server-related points of view) to install GNOME (or other DE) inside the server edition? or there is any counter-indications?
I searched around and I found that this command:

```
apt-get install gnome-desktop
```

is enough for GNOME installation. but, how can I set the server to start GNOME automatically at machine boot?

thanks thanks thanks for your time. :)

greetings

---

### Post by HermanAB on 2007-12-05
The Xfce system is far more efficient than Gnome or KDE.  So I suggest that you rather use that.  You can easily turn the desktop system on/off with 'sudo init 5' and 'sudo init 3'.  If I want a garden variety server, I simply use Xubuntu.

X listens on port 6000, but that is nowadays disabled by default, so there is no real security risk.  Use Firestarter to configure a basic firewall and read the iptables man page a few times.

Cheers,

Herman

---

### Post by var on 2007-12-05
first of all, thank you for your answer, HermanAB. :)
I searched around and I didn't find a server edition of Xubuntu.
so, in general, a DE is perfectly usable in a server environment?

thank you again for your time. :)

greetings.

---

### Post by aysiu on 2007-12-05
I would install IceWM:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by var on 2007-12-05
> **aysiu said:**
> I would install IceWM:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

a installation on low-RAM machines? RAM is not a problem... I'll install on a VMWare layer with at least a couple of GB of RAM.

thanks. :)

greetings.

---

### Post by rsambuca on 2007-12-05
> **var said:**
> a installation on low-RAM machines? RAM is not a problem... I'll install on a VMWare layer with at least a couple of GB of RAM.

thanks. :)

greetings.

This totally doesn't make any sense to me.  Why are you running a server within a virtual environment?

---

### Post by aysiu on 2007-12-05
> **var said:**
> a installation on low-RAM machines? RAM is not a problem... I'll install on a VMWare layer with at least a couple of GB of RAM.

thanks. :)

greetings.
Well, the guide is written for computers with low RAM, but it works for other machines as well.

Since the server edition doesn't install a GUI, and all you want is basically a server with a GUI, Gnome is a bit excessive. IceWM will give you a GUI and not a lot of other crap you don't need.

---

### Post by var on 2007-12-05
oh ok, so... another question: what are the differences between using Xubuntu and IceWM, in this case? under them, can I use all the applications I use under GNOME?

thanks again. :)

greetings.

---

### Post by aysiu on 2007-12-05
> **var said:**
> oh ok, so... another question: what are the differences between using Xubuntu and IceWM, in this case? under them, can I use all the applications I use under GNOME?

thanks again. :)

greetings.
Any application you have installed you can use in any environment.

Why do you need Gnome applications? I thought you were trying to run a server...

---

### Post by HermanAB on 2007-12-05
IceWM is coded better than Xfce, but speed and feature wise they are the same.  Xubuntu exists - Icebuntu doesn't - so just install Xubuntu and get it over with.

BTW, Linux *is* a server OS.  It doesn't matter what version you install to run a server, except that the WM tends to bloat things up a lot, so pick a light weight one (IceWM, Xfce, Blackbox, Enlightenment) that is all we are saying.

Cheers,

Herman

---

### Post by mellowd on 2007-12-05
If you're thinking about going into server management then the best way is to get your hands dirty in the terminal. I always find it better to learn the "difficult" way first.

---

### Post by var on 2007-12-06
ok, so I install the classic Ubuntu Server edition: then, what command I must use to install a minimal Xfce environment over it?

thanks to all. :)

greetings.

---

### Post by rsambuca on 2007-12-06
> **var said:**
> ok, so I install the classic Ubuntu Server edition: then, what command I must use to install a minimal Xfce environment over it?

thanks to all. :)

greetings.

You must first enable your software repositories using nano, and then you can install the xfce desktop package using:

sudo apt-get install xfce4

However, this seems rather pointless to me, as you could just use the Xubuntu install disc in the first place.  Also, the kernel for the Ubuntu Server edition isn't optimized for desktop use, so that is something to be aware of.  If you take the time to actually read the entire link that aysiu gave you, you would have seen that it gives you all of the required commands to install your desktop environment of choice.

---

### Post by mellowd on 2007-12-06
Also, as I said, in the real world 99.9999999% of linux server you'll work on have no gui. Therefore the best way to learn it is without any form of gui

---

### Post by doogy2004 on 2007-12-06
To answer you question with out including all of the debate about which gui you use or even to use a gui.  Each one of the following commands will install a gui and load the gui at startup.  The main difference that I can tell between the server and desktop editions is that the server kernel is compliled differently and at a fresh install the server is a command line driven and the desktop has a gui (you can install the desktop version without a gui by using the alternate disk and installing a base system)

GNOME (Ubuntu) 
```
sudo apt-get install ubuntu-desktop
```
KDE (Kubuntu)
```
sudo apt-get install kubuntu-desktop
```
XFCE (Xubuntu)
```
sudo apt-get install xubuntu-desktop
```

I learned by using the gui (GNOME) because I could perform an action and have it working, then I would go back and try to figure out how to get the same thing accomplished via the command line.  My reasoning is that if you use the gui you can learn what things are called then you will have a better understanding when you move to strictly command line.

I know these topics are debateable, But sometimes new users just need a simple answer rather than trying to sort through the bickering.

---

### Post by var on 2007-12-14
thanks to all. :)
@doogy2004: how can I automatically start the GUI Xubuntu environment at server startup?

greetings.

---

### Post by aysiu on 2007-12-14
If you have *xubuntu-desktop* installed, GDM (the graphical login screen or "display manager") should have come with it.

So type this in the terminal: ```
sudo /etc/init.d/gdm start
``` and that should do it.

---

