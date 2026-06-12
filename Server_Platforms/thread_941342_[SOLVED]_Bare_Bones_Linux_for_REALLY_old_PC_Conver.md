---
title: "[SOLVED] Bare Bones Linux for REALLY old PC Convert into Server?"
date: 2008-10-08
forum: Server Platforms
---

### Post by Black Razor on 2008-10-08
Ok,

So I have a REALLY REALLY old pc (win95 era gateway) that I want to just turn into a simple linux file server.  I have never worked with a linux server before, and I am looking for something that maybe I can remotely manage from my Ubuntu machine, leaving the server running just code with no gui.  

Anyone have any ideas which distro I should look at?  Again, I am starting to get the basics down with Ubuntu and am reasonably comfy with the CLI.

I have looked at and considered Slackware and EnGarde, but I believe EnGarde might be too system intensive for such an old machine, but dont really know if thats true.  Slackware as I understand it is bare bones linux at its best.  I have also considered the heckle of installing Puppy Linux to the Harddisk.

---

### Post by Black Razor on 2008-10-08
Speaking of Bare Bones....

[[IMG]http://img370.imageshack.us/img370/803/happyhalloweenlw9.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img370.imageshack.us/img370/happyhalloweenlw9.jpg/1/w373.png[/IMG]](http://g.imageshack.us/img370/happyhalloweenlw9.jpg/1/)

---

### Post by lykwydchykyn on 2008-10-08
If you're comfy with Ubuntu, Debian should do fine.  My home server is nothing but an old P2 350 with 320 MB of RAM.  It does samba, ssh, apache, mysql, dansguardian, squid, dictd, and dnsmasq all at the same time.  I can even do icecast on it, though that slows it down considerably.  It runs a GUI-less Debian etch.

---

### Post by cariboo on 2008-10-08
You could use the mini.iso to install to the commamd line, then use tasksel to install samba and nfs. the mini.iso is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Note: you need an internet connection to install with the mini.iso

Jim

---

### Post by amgalitz on 2008-10-08
> **Black Razor said:**
> Ok,
So I have a REALLY REALLY old pc (win95 era gateway) that I want to just turn into a simple linux file server.  I have never worked with a linux server before, and I am looking for something that maybe I can remotely manage from my Ubuntu machine, leaving the server running just code with no gui.  

I been running a at least a 12 year old system as a server with Gentoo, but I'm switching to ubuntu/debian since it is so SLOOOOOW compiling code and I'm sick of circular dependency blocks. (If you don't know what that is, be glad, very glad<G>) I run it headless most of the time (no keyboard or monitor attached).

I'd suggest giving Debian a try. It is what is under ubuntu when you drop to the command line in console mode. Nano is an easy text/terminal based editor that works over ssh. You can load putty to login over your network do command line (linux and windoze versions available) and thus do not even need to run Xserver. I compile new kernels from my main system through a putty session.

My server is a 400Mhz celeron, 512ram with 600G of IDE drives. I put a gigabit card in. You probably don't have pci slots so finding a fast network card might be tricky unless you are happy with 100Mb ethernet.

It would be more helpful if you list your exact hardware specs.

cheers

---

### Post by Iowan on 2008-10-08
My Breezy server is on a P200 HP Vectra VL.

---

