---
title: "[SOLVED] VMware Server does not support USB 2.0 / there someway to dumb-down Ubuntu U"
date: 2008-04-05
forum: Virtualisation
---

### Post by luvit on 2008-04-05
VMware Server does not support USB 2.0 / there someway to dumb-down Ubuntu USB ports?
[LIST]
[*]can anyone think of a way to force Ubuntu to think my USB ports are v1.1?
[*]some people have success using a v1.1 hub between their vmware and USB 2.0 device.
[*]i can't do that as USB hubs need to be powered for my device and i need the laptop to be portable for wireless surveys. ;)
[/LIST]

---

### Post by fsmithred on 2008-04-05
It works for me.

Open the vmware management console, click on the virtual machine you want to edit, then go to the menu bar, select VM, Settings, Hardware, Add, USB Controller, Finish, OK.

Then I followed the instructions that vmware gave me right before I clikcked OK. Power on the VM, go to the menu bar, select VM, Removable Devices, USB Devices, and there are no devices to select. Plug in the USB stick, go through that last bit of menu again, and it's there. Put a check mark in the box next to USB DISK 2.0. And it shows up on the desktop. If I look in dmesg or /var/log/kern.log, it says "new high speed USB device using ehci_hcd" which I think proves that it's really USB 2.0.

---

### Post by luvit on 2008-04-06
lulz... i dont' have any problems with anything you posted ;)

my probs are within the VM... i found it's a known issue that USB 2.0 devices are not fully supported by VMware Server... you must buy VMware Workstation...

A lot of people have found success by puttings a USB 1.1 hub between their PC and their USB 2.0 device... makes a lot of sense, however i can't walk around with my laptop and a powered USB hub to do wireless site surveys... (the powered USB hub would need an AC adapter... and extension cord).

i am hoping that Ubuntu can force my 2.0 USB ports to function at USB 1.1 specs... this will have nothing to do with VMware... i want to force my USB ports to function as USB v1.1 at my host OS level... Ubuntu

make sense?

---

### Post by fsmithred on 2008-04-06
I guess I don't understand what you can't do or what it is you're trying to accomplish. My knowledge on the subject is pretty much limited to my own setup - linux host with win xp vm, and a usb 2.0 stick that works in both operating systems. I didn't have to do anything to the linux side.

---

### Post by rogblake on 2008-04-06
> **luvit said:**
> 
i am hoping that Ubuntu can force my 2.0 USB ports to function at USB 1.1 specs... this will have nothing to do with VMware... i want to force my USB ports to function as USB v1.1 at my host OS level... Ubuntu

make sense?

Have you tried adding the ehci_hdc (USB 2.0) module to the blacklisted module list? This should leave just he uhci_hcd or ohci_hcd (USB 1.1) module loaded which will operate your ports in USB 1.1 mode. The situation is analagous to running Windoze 2000 or XP without the updates that support USB 2.0. (I have not tried it in Linux, but have observed this behavior in Windows systems. Might be worth a try.)

---

### Post by luvit on 2008-04-07
> **rogblake said:**
> Have you tried adding the ehci_hdc (USB 2.0) module to the blacklisted module list? This should leave just he uhci_hcd or ohci_hcd (USB 1.1) module loaded which will operate your ports in USB 1.1 mode. The situation is analagous to running Windoze 2000 or XP without the updates that support USB 2.0. (I have not tried it in Linux, but have observed this behavior in Windows systems. Might be worth a try.)

thanks... this didn't help me though. i'm sure it did what i wanted, but the VM still found it as a USB 2.0 device... and blue screen of death, as usual.

perhaps i can mode a VMware config... or the XP config within the VM to only believe that USB 1.1 exists and has no knowledge of USB 2.0

---

### Post by fjgaude on 2008-04-07
> **luvit said:**
> VMware Server does not support USB 2.0 / there someway to dumb-down Ubuntu USB ports?
[LIST]
[*]can anyone think of a way to force Ubuntu to think my USB ports are v1.1?
[*]some people have success using a v1.1 hub between their vmware and USB 2.0 device.
[*]i can't do that as USB hubs need to be powered for my device and i need the laptop to be portable for wireless surveys. ;)
[/LIST]

I'm not sure what motherboard or BIOS you have but in my BIOS of Gigabyte MB I can not activate the USB 2.0 portion, leaving the 1.1 only.

---

### Post by luvit on 2008-04-07
that is good thinking because i thought of it too :) lol
my bios has no USB options... ;)

i'm sure i'm thinking in a direction that hundreds of othes have already thought of... i may have to use a battery operated mini-hub... but it needs to be USB 1.1. Then plug my 2.0 device in it. i've seen several posts of people succeeeding this way.

I guess i should borrow a 1.1 hub and test before i buy a battery powered one. ;)

---

### Post by luvit on 2008-04-08
> **rogblake said:**
> Have you tried adding the ehci_hdc (USB 2.0) module to the blacklisted module list? This should leave just he uhci_hcd or ohci_hcd (USB 1.1) module ...)

SOLVED! Your blacklist recommendation did not help me... there's a good chance that I just don't know how to use the blacklist... a very good chance.( i added the line, saved the black list and rebooted.)
How i solved it is allot like what you recommended though ;)

How I solved it:
I  typed[COLOR="Blue"]** rmmod ehci_hcd**[/COLOR] in my Ubuntu host before I plug in my USB 2.0 device into my VMWare XP session.

3 questions... I have never used rmmod...[LIST]
[*]is rmmmod permanent?
[*]will ehci_hcd reload after a reboot?
[*]how do i manually reload ehci_hcd from the command-line?
[/LIST]

i give you thanks, rogblake!

---

### Post by OmegaBLK on 2008-04-08
> **luvit said:**
> 
3 questions... I have never used rmmod...[LIST]
[*]is rmmmod permanent?
[*]will ehci_hcd reload after a reboot?
[*]how do i manually reload ehci_hcd from the command-line?
[/LIST]



The **modprobe** command is the recommended way when inserting and removing kernel modules instead of rmmod & insmod.  Unless you blacklist a module, it will reload on the next reboot.  To load a module with modprobe:

```

sudo modprobe ehci_hcd

```

To remove a module:
```

sudo modprobe -r ehci_hcd

```

Of course you should check the man page for modprobe to make sure what I posted is correct as I am going off of memory here for the most part.

---

### Post by gatman3 on 2008-04-08
> **luvit said:**
> 

3 questions... I have never used rmmod...[LIST]
[*]is rmmmod permanent?
[*]will ehci_hcd reload after a reboot?
[*]how do i manually reload ehci_hcd from the command-line?
[/LIST]



rmmod is not permanent.  It only affects your presently running session.

To make the change *persistent* (note the subtle different compared with *permanent*, because you can always change it later)... Edit the /etc/modprobe.d/blacklist file and add the line:

blacklist ehci_hcd

To manually reload later, use modprobe:

sudo modprobe ehci_hcd

---

