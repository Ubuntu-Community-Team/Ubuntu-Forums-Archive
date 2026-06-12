---
title: "Ubuntu 20.4 login"
date: 2023-07-03
forum: Virtualisation
---

### Post by imaging2022 on 2023-07-03
Hi,

I use VMware Workstation 15 Player to run Ubuntu in Windows. Since 2-3 weeks, I am no longer able to login. Once I enter the password, it returns me to the main login page. I searched for a solution but unfortunately I can not log into the Shell to check the .Xauthority file as suggested by some people. I have Lenovo laptop and used Ctrl Alt F3 key combination with no luck. Any hints please?

Thanks in advance

---

### Post by DuckHook on 2023-07-03
I see three easy solutions:

[LIST=1]
[*]Press <Shift> or <Esc> during boot to reveal the hidden GRUB screen. From there, you can boot into safe mode or go to a console for repairs.
[*]Roll back to an earlier working snapshot. It might mean recreating some work, but if you have been snapshotting routinely, this should not be that much.
[*]Spin up a second Ubuntu VM, then connect the problematic VM's HDD and make repairs using the working VM.
[/LIST]

I do not use VMWare, so can't help you on specifics, but all VMs work alike in principle, so it's just a matter of working with the quirks of each platform.

Make sure you make yet another snapshot before monkeying around with the non&#8209;working one. This will allow you to experiment with solutions without getting lost in the changes you will be making.

---

### Post by MAFoElffen on 2023-07-03
For the VMware Workstation Hot-Keys:
```

Ctrl+Alt+spacebar     

Send any command to the virtual machine so that Workstation Pro does not process it. Hold down Ctrl+Alt as you press and release the spacebar, and continue to hold the Ctrl+Alt keys down as you press the next key in the combination. 

```
Not sure how you would press <Cntrl><F4> if you also then have to press <Cntrl><Alt> with that... That might take pressing <Left-Cntrl><Left-Alt><Spacebar>, then <Left-Cntrl><Left-Alt><Right-Cntrl><F4>... Is that physically possible? LOL  

When I install any Linux OS, especially VM's, I setup grub to force the Grub Menu to show, even if just for 2 seconds, so that I have a way in to rescue them.

---

### Post by MAFoElffen on 2023-07-03
Extending what DuckHook said, from the Grub Menu, you can choose Advanced Options > A kernel with rescue mode, or an earlier Kernel. If from a rescue mode, then select Enable Networking to mount the filesystem in rw, then select Root prompt...

Just may be me, but.... Rather than spending the extra time to create another VM to mount the affected VM's Virtual Disk image, I find it a lot faster to have the VM boot from a Live Installer ISO, and mount the installed system from the Live Environment. Quick and easy.

---

### Post by DuckHook on 2023-07-03
> **MAFoElffen said:**
> … Rather than spending the extra time to create another VM to mount the affected VM's Virtual Disk image, I find it a lot faster to have the VM boot from a Live Installer ISO, and mount the installed system from the Live Environment. Quick and easy.
Yep. That works very nicely too. I just assumed the OP has multiple VMs already installed because that's what I do (for redundancy, experimentation, safety, all sorts of crazy reasons). I also have powerful tools in those VMs that aren't part of a default install which would make diagnosis and repair a lot more convenient. But all of this is just me. If no other VMs, then MAFoElffen's suggestion is faster, easier and less hassle.

---

