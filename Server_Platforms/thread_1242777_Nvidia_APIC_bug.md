---
title: "Nvidia APIC bug"
date: 2009-08-17
forum: Server Platforms
---

### Post by ryandball on 2009-08-17
All,

I have been trying to resolve the APIC / Nvidia compatibility bug to no avail.  We have many servers that run Ubuntu, but this particular one is a fairly powerful desktop machine that I'm hoping to put into production as a fax server.  However, anytime I stress is more than just a little, it turns itself off.

Hardware: 
Motherboard: ASUS M3N78 Pro (Nvidia Geforce 8300)
CPU: AMD Athlon 64 X2 Dual Core Processor 5600+
RAM: 4 GB

OS:
Ubuntu 9.04 AMD64 (server install)
Kernel 2.6.28-11-server

Now I've run into this in the past, and it seemed I got it to work at some point, but I cannot here.  I cannot disable APIC in the BIOS (option is enabled and grayed out), I am running the latest BIOS from ASUS' website.

No matter what I try, I get this booting up:
*Your BIOS does not provide ACPI _PSS objects in a way that Linux understands.*

Once I see that, I know it's going to fail sooner or later.

The thing that really kills it is trying to start up a VM or trying to recompile the kernel; I had heard that possibly 2.6.30 would support the chipset natively.  But it always shuts off at some point during either process (loading a vm or running 'make' on the kernel recompile).

In /boot/grub/menu.lst I've tried every combination of 'noapic', 'acpi=off', 'lacpi=off', everything I can find in any combination, and it's like it just ignores me.  System works fine unless I stress it just a little, then it shuts off.

Any ideas???  I'd rather not scrap the hardware just because of this little thing if possible - new server hardware isn't in the budget right now, unfortunately.  I don't care about ANY power features, it's supposed to be a server so I would want it all disabled if possible.

current command line: root=/dev/mapper/hylafax-root ro acpi=off noapic quiet splash live

Thanks in advance!

Ryan from Portland

---

### Post by cariboo on 2009-08-17
I don't think you have an apic problem, I get the same sort of message at boot on my main computer, I daily start up vm's and have no problem. I would suggest you have a look at the hardware. If it is shutting down under heavy load, check the cpu and motherboard temps, and also check the power supply.

---

### Post by ryandball on 2009-08-17
You know I appreciate that - strangest thing.  Talk about not seeing the tree through the forest!  I was so thinking it was an APIC issue that that is all I focused on.

You mentioned power supply - well come to think of it, there are 6 disk drives (4 SATA and 2 ATA/133) and 2 RAID controllers, in addition to a serial PCI card.  Desktop power supply, 6 hard disks...  unplugged 2 of them (the 200 GB array) and so far I can recompile the kernel AND run VMs without hassle.  I bet if I bought a bigger power supply, I could run the additional 2 disks without a problem.

Talk about being a nancy!  Thank you for redirecting my mind!  I think this case is closed!

Ryan from Portland

---

### Post by cariboo on 2009-08-17
Your very welcome, I'm glad I could help.

I had the same misgivings when the error first popped up a couple of kernel version ago. I filed a bug and went through the error with one of the kernel devs, it is a bios problem that only an update from the manufacturer will cure. It won't cause any operational problems, so I've ignored the error ever since.

---

