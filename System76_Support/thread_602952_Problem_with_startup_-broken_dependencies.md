---
title: "Problem with startup -broken dependencies"
date: 2007-11-04
forum: System76 Support
---

### Post by miner on 2007-11-04
Hi !
My friend already has Ubuntu 6.04 on his laptop. It was working smoothly and without any problems. But just to get some more space on the partition, he removed some packages (which he thought were apparently unnecessary). he doesn't even remember which packages he had uninstalled.

Nothing happens then. He rebooted his computer and can only see a black screen with a pointer. The system doesn't give any error message of possible breakage of dependencies. And it seems nothing can be done further :(

Is there any way to diagnose and fix the problem from the linux prompt? Please guide.

Thanks

---

### Post by perce on 2007-11-04
try 
sudo apt-get install ubuntu-desktop

---

### Post by thomasaaron on 2007-11-05
So, it sounds like he doesn't even have a command prompt.
If that is the case, he may need to try to boot into recovery mode. When he sees the "grub 3...2...1...." screen, press the escape key.

Then highlight the first entry that has "Recovery Mode" in its description.

Once there, he can try Perce's idea. If that doesn't work, he might want to try

apt-get install -f    (or it might be apt-get -f install) I don't remember. This tries to fix broken dependencies.

Once this runs, enter:
reboot

---

### Post by perce on 2007-11-05
> **miner said:**
> 

Is there any way to diagnose and fix the problem from the linux prompt? Please guide.



From this I understood he had at least the command line. If he deosn't have even that and what Ton suggested doesn't work he can try to boot from a live CD and run apt-get install -f or apt-get install ununtu-desktop in a chroot.

---

