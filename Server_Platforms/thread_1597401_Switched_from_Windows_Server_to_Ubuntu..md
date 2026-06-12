---
title: "Switched from Windows Server to Ubuntu."
date: 2010-10-15
forum: Server Platforms
---

### Post by SirMeaky on 2010-10-15
Hey guys, 
I just need help on a couple of things.  As the title says I have been running Windows Server for around half a year and the time has come to switch it over to Ubuntu - which is now done.

What I have done so far:
1. Installed Ubuntu GUI.
2. Installed vnc4server.

What I cannot do:
1. Connect to the server via OpenSSH or VNC.  (I'm currently connecting through my host so I can give it commands via the CLI)
2.  Get neither VNC or OpenSSH working so I can connect directly to my IP address.

I basically just want to be able to use VNC to connect and do everything I need from there.

Any help would be appreciated, thanks guys :)

---

### Post by pricetech on 2010-10-15
Just to be sure, since you didn't say;  Do you have openssh-server installed ??  It should work right out of the box, so you shouldn't have to "configure" anything just to connect.

A recommendation I would have is to add NX from nomachine dot com to give you a GUI to work with.  Much better than VNC.

---

### Post by arrrghhh on 2010-10-15
Yea and networking questions ensue - is the box on your LAN?  We may be making assumptions about lack of firewall/WAN links...

---

### Post by SirMeaky on 2010-10-15
Hey, I've changed my mind I no longer require a GUI and yeah SSH was working out of the box.. Now it's all configured :D

The only thing now is setting up bind :D

---

### Post by annoyingrob on 2010-10-15
little known fact, X11 also works over SSH.

If you're SSHing into your linux server from another linux computer, specify the -X parameter (eg: ssh -X computername), and you can run graphical programs on your local screen from the remote machine. You won't have a complete desktop, but you acn type things like "firefox" into the command line, and have firefox display on your local machine, but running on the server.

---

### Post by HermanAB on 2010-10-16
Please, if you actually installed VNC on your server, do yourself a favour and make sure that it is properly disabled and not running, otherwise your sever will get hacked sooner or later.  

VNC is an evil POS and should not be lightly discarded - it should be thrown, with great force.

---

### Post by SirMeaky on 2010-10-16
Hey, thanks for all the tips.  I wont be needing X11 but thanks for letting me know!

Also in regards to VNC , I haven't installed it and wont be doing :)

---

### Post by Vegan on 2010-10-16
X11 belongs in a museum, there are better ways to do things now

---

### Post by bab1 on 2010-10-16
> **Vegan said:**
> X11 belongs in a museum, there are better ways to do things now
What are the "better ways" that you are referring to?

---

### Post by HermanAB on 2010-10-16
Xorg?

---

### Post by bab1 on 2010-10-17
> **HermanAB said:**
> Xorg?

The X Window System (commonly X or X11) is a computer software system and network protocol that provides a graphical user interface (GUI).  Xorg is one implementation of that:  *e.g. "The [**_X.Org project_**]("http://www.x.org/wiki/") provides an open source implementation of the X Window System. The development work is being done in conjunction with the freedesktop.org community."*

Vegan says there are *better ways* than X11.  I am assuming that he means the X Window System.  I am interested in what he thinks is a better alternative to the X Window System for Linux.

---

