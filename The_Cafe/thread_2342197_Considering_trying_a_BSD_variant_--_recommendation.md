---
title: "Considering trying a BSD variant -- recommendations?"
date: 2016-11-04
forum: The Cafe
---

### Post by kevdog on 2016-11-04
I'm considering trying a BSD variant within a VM.  The purpose of doing this is to get a real ZFS experience.  I have a flavor of a BSD experience on my Mac, but really want to get a real experience.  Things however such as writing firewalls are a lot different. Any idea where I should start?  I know FreeBSD seems like the biggest player, however I'm just wondering if this is the place to start.

---

### Post by bearlake on 2016-11-04
> **kevdog said:**
> I'm considering trying a BSD variant within a VM.  The purpose of doing this is to get a real ZFS experience.  I have a flavor of a BSD experience on my Mac, but really want to get a real experience.  Things however such as writing firewalls are a lot different. Any idea where I should start?  I know FreeBSD seems like the biggest player, however I'm just wondering if this is the place to start.

You likely have it there.

Tried GhostBSD and was happy with the results but it's a spin off FreeBSD.

---

### Post by &amp;KyT$0P# on 2016-11-04
I've played with a lot of BSD variants in VMs, and found NetBSD to be the easiest to install and set up.

The only way I could get a working FreeBSD was to start with their pre-installed VM image.

---

### Post by kevdog on 2016-11-05
Well I just started from the FreeBSD iso and have installed the base system and X window system and MATE as the desktop environment. Working with the port system vs the pkg system is interesting.  A lot of manual configuration in a lot of files although /etc/rc.conf mostly.  I set up an Arch install with bare metal and in a virtual box, and for everyone that complains about Arch, I'd have to say BSD is 10x longer, but not necessarily more difficult, just tedious particularly if installing from ports (which compiles the package and dependencies) vs the pkg system (which is pre-built binaries similar to what is distributed by pacman and apt-get).  All in all it's pretty interesting.

---

### Post by HermanAB on 2016-11-06
PC-BSD is prolly the easiest.

---

### Post by ArgentWarrior on 2016-11-06
I use FreeBSD on my home server and it works beautifully, but I don't recommend it for the desktop. I've tried using FreeBSD and DragonflyBSD as a desktop OS, and IMO they kinda suck there. Gentoo with i3wm is more comfy. It doesn't throw a fit when I switch to a VT from my X session and back, and the audio doesn't suck.

---

### Post by kevdog on 2016-11-06
I'm having my head wrapping my head around the port system.  I understand the difference between the pkg system (binaries) and port (install from source), however -- the port things is such a pain in the ass.  Compiling these from source takes a long time, it's definitely not automatic, and I have figured out a great way to check for upgrades and then actually upgrade with minimal interaction.  The pkg system is a little bit more like linux package management (apt, pacaur), however not everything is available with the pkg system.  Any tips would be appreciated.

---

### Post by montag dp on 2016-11-07
I ran FreeBSD on a VM for a little while. It was an interesting experience. I was looking for a laptop OS, though, and I never installed it to bare metal because it sounded like it would not be worth it from the perspective of hardware compatibility. For a server, it would probably be a good choice. I ended up with Slackware for the desktop, which is perfect for me.

---

### Post by Dragonbite on 2016-11-07
I'm using FreeBSD at work as a headless web server.

Chances are a desktop BSD would give you a better interface to run things and as you get more used to it you can move down into the command line at a comfortable pace.

---

### Post by 1clue on 2016-11-07
If you want a firewall-oriented BSD variant then you might try pfSense.

---

