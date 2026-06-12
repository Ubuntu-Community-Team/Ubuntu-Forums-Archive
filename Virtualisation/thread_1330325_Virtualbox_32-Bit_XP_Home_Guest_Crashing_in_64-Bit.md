---
title: "Virtualbox: 32-Bit XP Home Guest Crashing in 64-Bit Xubuntu Host"
date: 2009-11-18
forum: Virtualisation
---

### Post by Mhoram on 2009-11-18
I've installed virtualbox on my 64-bit Xubuntu 9.04 system, and a 32-bit XP Home guest inside that.  Everything works: I can access the network, hear audio, mount discs and use shared folders, but the XP guest generally crashes within 5-10 minutes.  It doesn't harm the host, and I can restart the guest as many times as I like, but then it just crashes again.  There doesn't seem to be a specific action that makes it crash; sometimes I'm running a program, and sometimes it's running in the background and suddenly goes down.  It seems like when I first installed it a few days ago, it wasn't this flaky, but now it's unusable.  I thought maybe I'd picked up a virus already, but Avast finds nothing.

I tried removing virtualbox and installing the non-free virtualbox-3.0, and that didn't make a difference.  As far as I've been able to find out, running 32-bit guests on a 64-bit host shouldn't be a problem, but I'm not sure where else to look.  I suppose my next move will be to wipe out the whole thing and start again, in case some other update is messing up virtualbox.  Any known problems like this, or other suggestions?

System is a dual-core AMD x64 with 5GB RAM, with 2GB of RAM and 10GB of drive space allocated to virtualbox.  The guest is standard XP Home, not registered yet because I want to make sure it's going to work before I go buy a copy.

Thanks.

---

### Post by daleslcap on 2009-11-19
I am having a very similar experience.  A boot to Ubuntu and then a vmware in firefox with XP was working well on my 64 bit AMD with 9.04 . Now I have upgraded to 9.10 the vmware powers off on its own after a few minutes.  

When upgrading I had to find work a rounds for Xserver on nvidia and mouse grab issues.  

I had to rebuild vmware as expected.

I haven't found a way to stop it from powering off.

I have some work applications I need that only run under XP.


Any help would be appreciated.

---

