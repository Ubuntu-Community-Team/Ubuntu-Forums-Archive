---
title: "Installed 20.04, unable to load grub"
date: 2020-04-03
forum: Ubuntu Development Version
---

### Post by dmak1000 on 2020-04-03
just replaced 16.04 with 20.04 beta and grub unable to load (it was fine with 16.04 where I dual boot with Windows). Now I am forced into 20.04 every time. I have run boot repair and still no grub menu (.txt below). Any ideas?
[FONT=&quot]
[https://paste.ubuntu.com/p/xsdyCQZMPW/](https://paste.ubuntu.com/p/xsdyCQZMPW/)


[/FONT]

---

### Post by yancek on 2020-04-03
Ubuntu 20.04 is beta which means that by installing it, you have volunteered to test it.  Probably will be a number of things that need to be ironed out before a full release.

You have a Legacy install of windows and you appear to have an EFI install of Ubuntu.  You can verify this by booting Ubuntu and from a terminal running the command below and check the output.

> [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

Ubuntu Grub installed in EFI mode will not boot a Legacy install of windows.  Reviewing the boot repair output, you can see that the EFI partition does not contain any windows EFI files so it won't boot UEFI. Boot repair also shows that you left windows hibernated and therefore, even if everything was done correctly with the Ubuntu install, Ubuntu would not mount any windows partitions and therefore would not create a boot entry for windows (see lines 514-518 in boot repair. 

Problems dual booting windows and Ubuntu UEFI particularly mixing Legacy and UEFI installs are explained at the Ubuntu documentation at the site linked below. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Frogs Hair on 2020-04-03
Moved to *Ubuntu Development Version.*

---

### Post by dmak1000 on 2020-04-03
Looks like my ubuntu is in legacy mode (see below output)

pc-ubuntu:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Legacy boot on HDD

My motherboard supports both legacy or UEFI boot, however when I go in and select my windows drive as priority boot I am still getting Ubuntu boot (I have two SSD one with windows installed one with ubuntu). Remember previously when I was on 16.04 grub will load and i can select ubuntu, windows, and i bunch of other stuff memtest...etc. But since I replaced it with 20.04 i am forced to boot it only. is this a 20.04 issue?

In a desparate move I tried installed 18.04 alongside just to be hope it can fix my boot but while installation was successful I can still ONLY boot into 20.04 and no grub still. see boot-repair output below:

[https://paste.ubuntu.com/p/mCqG6wJMRy/](https://paste.ubuntu.com/p/mCqG6wJMRy/)

just a bit more background my windows install start as win7 (and therefore legacy) and then upgraded to win10. I have changed various hardware (motherboard, cpu, harddisk) but the win install remains. 

finally how do I wipe my 20.04 install if I can only load into it at the moment?

thanks all

---

### Post by dmak1000 on 2020-04-03
OK I ran boot-repair again while in ubuntu and in advanced option I asked it to restore MBR on my windows boot partition and now I can boot up windows, but no way to boot ubuntu now. see output below

[https://paste.ubuntu.com/p/gztP2zTKTv/](https://paste.ubuntu.com/p/gztP2zTKTv/)

I read somewhere I may convert windows legacy install to a EFI install. do you think it's a solution to get grub too work? im still confused as to why grub worked before but not now....

---

