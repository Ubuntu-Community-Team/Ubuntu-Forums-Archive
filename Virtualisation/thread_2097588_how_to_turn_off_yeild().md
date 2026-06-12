---
title: "how to turn off yeild()"
date: 2012-12-23
forum: Virtualisation
---

### Post by agrayray on 2012-12-23
I was fooling around with a virtual machine and set it to use two processors..when I tried to start it with vmware workstation..I got a message saying...

[FONT=Courier New]
The host's  Linux kernel yield() functionality is disabled. Multiprocessor virtual  machines exhibit degraded performance without yield(). Choose 'OK' to  enable the sysctl 'kernel.sched_compat_yield' or 'Cancel' to continue  without yield()[/FONT]

I choose yield() option but now I want to disable as I believe now my whole system is running a tad slower and it didnt make any difference in my vm...

I am running Ubuntu 10.10 GNOME...does anyone know how I turn this off again?

I checked some forums and it says to edit the 

Add this line to the [FONT=Courier New]/etc/sysctl.conf[/FONT] file:

[FONT=Courier New]kernel.sched_compat_yield=

[/FONT]setting..

but when I checked this file I didnt find the setting...? 

? 

Thanks in advance[FONT=Courier New] 
[/FONT][FONT=Courier New]
[/FONT]

---

### Post by howefield on 2012-12-24
Thread moved to the "*Virtualisation*" forum.

---

