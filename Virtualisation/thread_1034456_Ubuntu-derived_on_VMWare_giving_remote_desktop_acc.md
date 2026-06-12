---
title: "Ubuntu-derived on VMWare giving remote desktop access to LAN clients"
date: 2009-01-08
forum: Virtualisation
---

### Post by mbarne on 2009-01-08
Hello,

I wrote an howto/guide to install a Ubuntu-derived distro on VMWare server and configure it to allow remote desktop connections from other computers in LAN.

Give me your opinions : [Linux Remote Desktop HOWTO]("http://www.crystalsolutions.it/?q=node/13")

Bye

---

### Post by HermanAB on 2009-01-08
Hmm, the easiest way to run remote X applications from Windows is with PuTTY and Xming.

Then you simply launch gnome-panel or KDE kicker and go click happy.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-01-08
> **mbarne said:**
> Hello,

I wrote an howto/guide to install a Ubuntu-derived distro on VMWare server and configure it to allow remote desktop connections from other computers in LAN.

Give me your opinions : [Linux Remote Desktop HOWTO]("http://www.crystalsolutions.it/?q=node/13")

Bye

Remote log in is fun. Once you learn the command line you can use just ssh and screen. You can forward the occasional X application if needed.

Your how-to is fine, but there is always the temptation to then open a port on your router and allow access over the Internet. This is where security comes in ...

VNC is insecure, I advise you look at FreeNX or tunnel over ssh.

SSH, IMO, also needs to be locked down.

Take a look at 

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

At any rate, enjoy.

---

### Post by mbarne on 2009-01-09
Hi,
thank you for your comments.

You're right, the "temptation comes"... I opened a port indeed.... but fortunately only for testing purpose, then sanity came back to my mind and I reverted to a "close" network. :D

---

### Post by mbarne on 2009-01-09
Anyway, what was "interesting" for me was permitting lan users (probably using win machines...) to have a linux desktop without having the need to dedicate a pc only for it 
(yes, I know that it would be a better solution... but seemed quite nice/strange to me to virtualize the linux server inside a winxp machine... I wanted to give it a try ;) ).

Bye

---

### Post by bodhi.zazen on 2009-01-10
> **mbarne said:**
> Anyway, what was "interesting" for me was permitting lan users (probably using win machines...) to have a linux desktop without having the need to dedicate a pc only for it 
(yes, I know that it would be a better solution... but seemed quite nice/strange to me to virtualize the linux server inside a winxp machine... I wanted to give it a try ;) ).

Bye

I agree that is very cool. Linux is designed to be multi user and your idea should work fine.

ssh -X allows you to forward a single application, rather then the whole desktop, and you may enjoy that as well.

---

### Post by bodhi.zazen on 2009-01-10
> **mbarne said:**
> Anyway, what was "interesting" for me was permitting lan users (probably using win machines...) to have a linux desktop without having the need to dedicate a pc only for it 
(yes, I know that it would be a better solution... but seemed quite nice/strange to me to virtualize the linux server inside a winxp machine... I wanted to give it a try ;) ).

Bye

I agree that is very cool. Linux is designed to be multi user and your idea should work fine.

ssh -X allows you to forward a single application, rather then the whole desktop, and you may enjoy that as well.

---

