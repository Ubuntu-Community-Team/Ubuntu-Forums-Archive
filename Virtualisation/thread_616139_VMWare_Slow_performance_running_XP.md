---
title: "VMWare Slow performance running XP"
date: 2007-11-17
forum: Virtualisation
---

### Post by 5h4rk on 2007-11-17
Hi, my XP virtual machine is about 13GB, I made it out of my current running Windows. When I start the virtual machine, XP takes ages to start up and I can't do anything because it's too slow. Is that because my virtual machine is too big? Should I do a fresh installation? Or is there something else that I'm missing?

Thanks

---

### Post by Shazaam on 2007-11-18
When I virtualized my physical WinXP install it ended up being about 19gigs so yours sounds about right. Also I only allocate 512mb memory for the vm as any more seems to slow the whole system down.
Have you gone into "Device Manager" and looked for any problems there? Already installed chipset drivers and such can cause problems. Another problem can be fixed by changing the processor in Device Manager from "Uniprocessor PC" to "Standard PC"  to fix any acpi problems, but if you have already activated your XP vm you will have to do it again after the change. When you change it to "Standard PC" WinXP will rediscover all of your virtual hadware.

---

### Post by dpj23 on 2007-11-18
I would recommend that you use a minimum of 512mb RAM...  And install VMtools into the guest operating system...   This will also improve performance...

---

### Post by tighem on 2007-11-19
Same problem for me until I switched to Virtualbox 1.5.2. Much faster than VMWare server.

Virtualbox is not without its problems, but if you just need to run XP applications it's pretty fast.

---

