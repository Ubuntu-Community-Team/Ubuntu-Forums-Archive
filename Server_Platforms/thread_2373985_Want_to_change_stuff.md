---
title: "Want to change stuff"
date: 2017-10-11
forum: Server Platforms
---

### Post by freddy58 on 2017-10-11
I have an Older Desktop sitting here running Freenas right now.  Would kicking Freenas off the disk and installing Ubuntu Server help me in which ways?  Ubuntu Server Software is so I post web pages, Am I correct in saying that?  It is not NAS software?  Right now, this Computer has one 500 GB Hard drive in it (On Disability, things take time to upgrade), if I installed Ubuntu Server Software, could I add More 2 or 3 TB Hard Drives.  The computer has space for about 8 Hard Drives, and I have the SATA ports available to put that many in.

---

### Post by ian-weisser on 2017-10-11
Ubuntu is a Linux operating system. You can use it to run a server, you can use it to run a storage farm, you can use it to run a desktop, you can use it for a lot of things.

---

### Post by freddy58 on 2017-10-11
I am not talking about Ubuntu OS, I am talking about Ubuntu Server software OS.

My Main computer, which sits right to the left of the one mentioned above, runs as its on OS, Linux Mint 18.2 Sonya Cinnamon

---

### Post by ian-weisser on 2017-10-11
It's the same OS.
Ubuntu Server is merely one flavor of Ubuntu.
The packages are identical in all flavors.
The packages are shuffled slightly differently to create different flavors.

You can easily convert Desktop to Server to different Desktop with just a few commands.
You can easily have one system run a desktop and a server and a storage farm and a VM farm...if you really want to.

---

### Post by wildmanne39 on 2017-10-11
*Thread moved to **Server Platforms for a better fit**.*

---

### Post by LHammonds on 2017-10-12
Ubuntu Server is basically the Ubuntu Desktop but without the desktop GUI and additional applications.

Consider Ubuntu Server to be the base OS without anything extra.

You "could" install the Ubuntu Desktop GUI if you want but if you are setting up a server / service, it is typically more secure to NOT run a GUI which adds additional surface area for attack.

To manage the server, you typically Telnet / PuTTY into it which requires having OpenSSH installed as part of the base OS.  Otherwise you will need to access it directly via the console but that is pretty-much the same thing you'd see if connected remotely via Telnet / PuTTY...which is a command prompt.

I run several production-level servers and have documented how I install Ubuntu Server that can be maintained over a long period of time (check my sig)

LHammonds

---

