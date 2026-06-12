---
title: "Virtualbox HELP!"
date: 2008-04-22
forum: Virtualisation
---

### Post by justagamer on 2008-04-22
I installed virtualbox ose modules for kernel 2.6.24 and after i rebooted my wireless card is no where to be found and my audo isn't working at all (besides system beeps). But i can get online with a direct connection to my router. Other then the audio and wireless everything else (as i can see) is fine.

---

### Post by jbrown96 on 2008-04-22
What are your wifi and audio cards/drivers?

---

### Post by justagamer on 2008-04-22
I fixed it thanks anyways though :)

---

### Post by poet_will on 2008-04-23
How did you fix it?  I'm having the same problems.

---

### Post by poet_will on 2008-04-23
Ok, I did some research and I also fixed the issue of no wireless.  The problem is that for some reason VirtualBox pulls down the -386 kernel.  So, when I restarted the computer booted into the -386 kernel and I lost the wireless.  All I did was rebooted again, and chose the old kernel (-generic) in grub and booted.  I now have wireless back and everything is as it should be.  I then un-installed the -386 kernel through synaptic.

---

