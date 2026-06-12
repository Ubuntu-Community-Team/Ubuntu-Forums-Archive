---
title: "Reboot and Select proper Boot device"
date: 2012-08-13
forum: Server Platforms
---

### Post by drewbuntu2 on 2012-08-13
Hello all,

I'm trying to install Ubuntu 12.04 LTS on a newly-built server machine, but I'm having trouble getting it to boot.

I go through the installation, leaving things on their default options, with the exception of setting things up for a four-disk software RAID 5 set up (as per the instructions from [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)).  Installation seems to proceed normally until the end, when the computer reboots and I'm greeted with "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

This is the same message I'm greeted with before any OS has been installed.  I have gone into BIOS to ensure that the HD is one of the boot options (it is,) and set it to the first boot choice for good measure.  The problem persists even if I reinstall on just one HD without setting up any RAID.

This is a newly built machine with no other OS installed.  I may as well mention that the motherboard's capable of doing some kind of fake RAID, but I haven't set that, opting instead to setup RAID through Ubuntu (which I understand is a better way of doing it.)

Any help you can give me in fixing this issue would be greatly appreciated!  Let me know of any further info / experimenting I can provide that will be enlightening.

Many thanks!

The computer specs are below:
Mobo: ASUS KGPE-D16
CPU: 2 x                               AMD Opteron 6212
RAM: 8 x 8GB 240-Pin DDR3 SDRAM DDR3 1333 ECC
HD: 4 x  2TB 5900 RPM SATA 6.0Gb/s[B][URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16822148681"]
[/URL][/B]

---

### Post by carldash92 on 2012-10-28
This is my first time ever doing anything with Linux and I was in the exact same situation as you.

I followed the guide as per you link and could not get it to boot afterwards.

After spending a long time searching the internet I found something that said to try the following:

When creating the partitions, go to Manual as normal, select each disk and say create new partition. Now when you select the Free Space, select the automatically configure. Repeat for all drives and then continue the manual as per normal.

---

