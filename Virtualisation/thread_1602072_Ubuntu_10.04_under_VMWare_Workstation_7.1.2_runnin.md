---
title: "Ubuntu 10.04 under VMWare Workstation 7.1.2 running wine 1.3.5 warcraft 3"
date: 2010-10-21
forum: Virtualisation
---

### Post by ngsngn on 2010-10-21
Hi all,

not sure if it is the correct place to post here. If no, can the moderators please move it to the correct place.

Basically i'm using VMWare workstation to emulate Ubuntu 10.04 and Win XP SP2. I tried warcraft 3 on both of these 2 virtual machines, for Win XP SP2, the game can run. However for Ubuntu 10.04, running the latest wine 1.3.5, i had trouble getting the game to run even after updating to the latest patch which require no cd, i got a no cd rom error, but after some googling, i suspect is a video driver problem but do not know how to solve it. Help is needed here.

FYI, a physical install of Ubuntu 10.04 with proprietary linux ATI driver on my another partition the game work as per normal, so i suspect is Ubuntu unable to 'find' out the video graphics, i do not know where to check in Ubuntu as well as i am new to linux.
I had also enable 3D acceleration in the VMWare.

my system configurations is as follow:

C2D E6750
2GB RAM
ATI HD3870 512MB

Any help is appreciated, thanks!

---

### Post by ngsngn on 2010-10-22
after running through the command line with -opengl, i got this error:

err: ole:CoCreateInstance apartment not initialised
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  964
  Current serial number in output stream:  965

---

