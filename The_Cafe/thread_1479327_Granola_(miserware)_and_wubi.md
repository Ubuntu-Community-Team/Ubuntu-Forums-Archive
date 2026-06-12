---
title: "Granola (miserware) and wubi"
date: 2010-05-10
forum: The Cafe
---

### Post by DogMatix on 2010-05-10
I have a netbook with a wubi install of Lucid and obviously with a netbook battery life is an issue especially when roaming around. So I became interested with the Granola power saving software. So I have basically two questions on my mind, those being:

[LIST][*]what are your general views/experiences of the Granola software;[*]will a wubi install work OK with it (as a wubi install doesn't hibernate) or will it function fine?
[/LIST]

Thank you

DM

---

### Post by PacketCollision on 2010-06-03
My understanding of Granola is that it simply monitors CPU usage and adjusts it appropriately using the standard sys interface to the userspace cpufreq driver.  It should work just as well in Wubi as in a normal install.  

Just remember that Granola is closed-source software, so we cannot check and make sure that the software isn't doing anything else.  You have to take MiserSoft at their word that their software is safe and does what is advertised.

---

### Post by Artemis3 on 2010-06-05
It also deletes the init.d scripts to use the ondemand governor, leaving the system in Perfomance should you later decide to uninstall it...

IMO it uses more energy for normal use than ondemand, except when a process hogs the cpu for a while since the granola userspace governor lowers the frequency after a while of full usage (meaning your video encodings will be slowed a lot!).

So i advise against it, the kernel governors are better :)

---

