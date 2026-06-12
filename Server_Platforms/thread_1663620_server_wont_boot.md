---
title: "server wont boot"
date: 2011-01-09
forum: Server Platforms
---

### Post by alliance1975 on 2011-01-09
I believe I successfully loaded server from a usb stick onto a 16gb compact flash, via cf to ide adapter. My early attempts couldn't get past language selection, but I changed the 80 conductor ide cable to a 40 conductor and the process apparently went to completion. But upon re-booting I get:

Verifying DMI pool data...................Update Success
Read Error_

I have reloaded multiple times and plugged the cf into my ubuntu laptop and used Gparted to erase all partitions from the cf and reloaded only to get the same error message. I would gladly try any commands to gather information on the problem but I can't seem to use the usb stick to get to a prompt to examine the cf. Gparted showed the typical partitioning but for some reason I can't get it to boot. Can someone hep me please.

BTW this is not an upgrade, not a dual boot, only one cf card for a hdd. this is a fresh install.

---

### Post by alliance1975 on 2011-01-10
Can someone please provide help on this. The install process seems to go to completion without a hitch, it just won't boot. I will try to get any information requsted. I can hook the cf up to my existing ubuntu laptop and run any commands, I just can't get past the Read Error statement.

---

### Post by chrislynch8 on 2011-01-10
This is an obvious question, but is your Usb Key bootable? Can your Laptop boot to a USB-Key

---

### Post by alliance1975 on 2011-01-10
I have not tried a usb boot with my laptop since it has a cd/dvd player/burner, but I have successfully used a usb stick to load ubuntu 9.04 on to my sons netbook and all worked well. I did use my laptop to create the 10.10 server bootable usb stick. This stick is what I used to load server onto a third small computer equipped with a 16gb compact flash card in a cf/ide adapter. The cf is the only hdd on the system. Server loaded from the usb stick seemingly without a problem, (i.e. it went all the way to grub install and reboot). And that's when the read error appeared. Except for the cf card the existing computer is operational, (a hdd with win xp boots and operates without problem). I can attach the cf to a hdd reader and connect it to my laptop and can see the cf contents, (one of my attempts to fix the situation was to use Gparted to completely wipe the cf and start server reload from scratch). I must assume server loaded onto the cf in a basic configuration, I selected minimal install guided using whole drive, Iplan to add 2 500 gb raid 1 drives later when I get server operational.

BTW, I almost forgot, Thank you for any help you may provide.

---

### Post by alliance1975 on 2011-01-10
Well, I loaded ubuntu server yet again, this time from the cdrom. I got past the read error and now all I have is:

grub>

and nothing else.

Can anyone please help.

---

### Post by alliance1975 on 2011-01-10
in grub i entered root and got
(hd0,msdos1): Filesystem is ext2

Should this be?

---

### Post by alliance1975 on 2011-01-12
Problem solved, server boots without problem.

---

### Post by casylum on 2011-04-14
How did you solve your problem?

---

