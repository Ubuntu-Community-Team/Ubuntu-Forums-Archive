---
title: "virtualize Windows XP for VPN"
date: 2008-01-17
forum: Virtualisation
---

### Post by scamper_22 on 2008-01-17
Hi all,

I haven't had much like getting checkpoint secureclient VPN working on gutsy, so i;m going to try and just run windows in a VM.

Keep in mind, I won't be doing much from the windows VM...just VNCing into my work computer.

What VM would people recommend?
Vmware, QEMU

Do you think my laptop has enough ram/CPU to run it?
it is a AMD64 3000+ CPU with 512 MB/RAM.

Just runnning Gutsy with a browser/IM open takes up about 250MB
Can your run windows XP virtualized in 128 MB RAM?

Are there any complications I should watch out for.  I am connected to the internet via a wireless setup.

Thanks,

Y

---

### Post by dark_phantom on 2008-01-17
I use virtual box and was successful in installing windows xp.  512 MB seem a bit low, but you can go ahead and try it.  Make sure you met the requirements for windows, whether 128 or 256 MB.  Virtual box was pretty easy to install and configure to use.  Good luck.

---

### Post by p_quarles on 2008-01-17
I agree with dark_phantom that Virtualbox is the most user-friendly VM.

128 MB of RAM is the minimum for Win XP, and I have an old box that used to run XP with exactly that -- until I upgraded to SP2. That knocked the wind right out of it. Following that, it ran about the same on 384 MB. So, if you're planning on running SP2, you're either going to want more memory, or you're going to need to do a lot of tweaking. 

I run XP-SP2 in Virtualbox on my current machine (Pentium D 2.8GHz, 1 GB RAM) and dedicate 512 MB of memory to the VM. Windows runs fine with this setup, but I get a *lot* of slowdown from swapping in the host OS while Windows is running.

---

### Post by scamper_22 on 2008-01-18
Hi,

thanks for the virtual box recommendation!
It worked perfectly.

The only thing I wish I'd known is when you launch virtual box, you can install the some additional plugins/packages(forget the name right now...just explore a session's menus).  Once I did that, everything worked perfectly.

Speed is not too bad either.  That's actually surprising :P
Besides, not having enough CPU/mem to launch needless games/applications might make me more productive when i work from home :P

---

