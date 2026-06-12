---
title: "Please cant use vncserver"
date: 2007-12-20
forum: Server Platforms
---

### Post by volkswagner on 2007-12-20
Please forgive me, this is a double post see here

[http://ubuntuforums.org/showthread.php?t=645169]("http://ubuntuforums.org/showthread.php?t=645169")

I can't get a readable screen via vncserver.  I am sure it is a problem on the server  machine as I can get a good session from a separate machine on the network.  

I also think It has to due with video setting on the server since I am using propriatory drivers to get the svid out working.  Although I did not try connecting the svid while using free drivers I assumed I needed to enable propriatory to get the svid out.  Anyway what can I do to get a readable image via vnc?

Please understand the physical location of the machine makes it very difficult to access and add a monitor even temporary.  So it is a must to get this working.

---

### Post by HermanAB on 2007-12-20
Use SSH.  It is easier to set up, more useful and secure.

VNC is mainly for people who don't know how to use SSH properly...

Cheers,

Herman

---

### Post by lmahoney on 2007-12-20
I"ve tried vncserver. It was really slow. I think it sends bitmaps over the network. I agree with Herman, ssh is a better option. Have you taken a look at Free NX from nomachine.com?

---

### Post by HermanAB on 2007-12-20
Connect with SSH, ensure that X forwarding is enabled and run any program you want directly, or if you are click happy, run the gnome panel or KDE Kicker.  

Here are some examples:

ssh -X -c blowfish user@server

ssh -X -c blowfish user@server "gedit /etc/fstab"

ssh -X -c blowfish user@server kicker

ssh -X -c blowfish user@server gnome-panel

Cheers,

Herman

---

