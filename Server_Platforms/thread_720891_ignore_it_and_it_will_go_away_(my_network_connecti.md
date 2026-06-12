---
title: "ignore it and it will go away (my network connection)"
date: 2008-03-10
forum: Server Platforms
---

### Post by psilo on 2008-03-10
I just installed server edition on an old Toshiba Portege 3480CT.  The installation went fine and I've got networking up and running on a wired connection.  I've been using ssh to remote into the machine.  Everything works fine as long as I keep using the connection.  If I let it sit for too long without using it, the laptop drops it's network connection.  If I go over and tap the keys on the laptop, suddenly I can ping it again.  I'm assuming this is some kind of power management kicking in but I don't know enough about changing the PM configuration from the command line to do anything about it.

Anyone run into this before?

---

### Post by netlogic on 2008-03-10
try acpi=off command to the kernel

---

### Post by psilo on 2008-03-11
Thanks.  I'll try that when I get home.  Will I be losing anything else by turning ACPI off?  This machine will be on all the time and I'm trying to keep the power consumption down.

---

### Post by jonabyte on 2008-03-11
check the bios for any energy saving features, not sure if this effects the server edition, but its the only thing that comes to mind.

---

### Post by netlogic on 2008-03-11
> **psilo said:**
> Thanks.  I'll try that when I get home.  Will I be losing anything else by turning ACPI off?  This machine will be on all the time and I'm trying to keep the power consumption down.

Yes, you will lose the advance power management, because you are turning ACPI=OFF at the boot time. This is a server, so it is all about the availability.  If you want to save power on the server, you can lower the watt goes into the cpu by playing with the cpu scaling and place the drives to a sleep mode by using hdparm.

example: force your drive to go into a standby mode.
hdparm -y /dev/hda
--or---
hdparm -Sxxx /dev/hda
go standby after certain xyz length of time.

type "man hdparm" for more detail

---

### Post by psilo on 2008-03-17
Ok, things have changed a bit.  I trashed the Toshiba.  It was old and loud and I decided to use a Latitude D600 I had sitting around instead.  I've loaded Hardy server alpha 6 on it and I still have the same problem.  If I leave the network connection idle for too long, the machine becomes unreachable on the network until I go and initiate some network activity from the laptop (ping the router - whatever).  Then I can suddenly ping the laptop again.  

This is making me nuts.  I've looked in the BIOS and found nothing I can relate to this.  I've added noacpi to the kernel options and the problem remains.  I'm open to suggestions...

---

### Post by netlogic on 2008-03-17
Since you haven't mentioned this to us. Are you running a Gnome Desktop Manager? Are you running a Desktop environment as a server? If you are, turn the power manager OFF. Your bios and board might not support ACPI under Linux.  Your vendor might not have released the drivers for Linux. It is really hard to reverse engineer every chipsets for all the PC boards. There must be over 75,000 different boards made since the 80s, least 1000 chipsets (north and south) from various companies.  I know I said this before. I am a fan of graphical environment for servers. It causes  more problems than it solves. Also, turn your screensaver OFF. If you aren't running a desktop environment, it is definitely bios related. Since you told the kernel to turn off ACPI during the boot. It seems to me, your machine is constantly going to S3 mode and crashing somewhere and it isn't overriding the bios information.

so no GNOME: BIOS related
1. update your bios
2. re-configure your bios
3. turn off acpi during kernel

with Gnome
1. get rid of sleep features from Gnome
2. turn off screensavers (in case you have a corrupted installation)

=========================
if you have tried everything, please post your dmesg to us.

---

### Post by netlogic on 2008-03-17
One more thing. You can also try the opposite by acpi=force or acpi=strict. 

Also, I don't know what devices running on your machine without the further information.
Try pci=noacpi or acpi=noirq.

strict - things less tolerate that isn't ACPI compliant
force - works for older bios. such as before year 2000
pci=noacpi - No irq routing through NEW ACPI SYSTEM
acpi=noirq - don't use acpi for irq routing.

---

### Post by psilo on 2008-03-18
No gui installed.  I've tried acpi=off, acpi=force, and pci=noacpi.  The BIOS I'm using is the latest one and the the only power related things I can find in it are screen brightness, Speedstep (enabled), and wake on lan (disabled).  No matter what I change, the same problem comes back.  I've attached a lshw report and a dmesg.  The dmesg if from when the machine was booted with the acpi=force kernel option and taken after the network stopped and was brought back by pinging my router from the laptop.

Thanks for all the help...

---

### Post by netlogic on 2008-03-20
few suggestions
1. add this to your kernel "pci=routeirq" try two different approach. your dmesg says, it can't detect ACPI.  NetXtreme BCM5702X should be supported device. However, you are currently using Tigon3 chipset driver for your Ethernet. I'm not sure that is the right one. I never experienced or seen your hardware, so I wouldn't know. You might get a better answer searching around the net or emailing your vendor technical support about your hardware.

[LIST]
[*]acpi=off pci=routeirq
[*]acpi=force pci=routeirq
[/LIST]

Try both 

2. also disable your bluetooth for now.

Also, explain to us about your bios settings. Did your current bios setting worked with Windows?

---

