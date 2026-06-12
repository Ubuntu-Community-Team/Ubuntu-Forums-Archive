---
title: "Ubuntu 18.04 Grub a Total Mess"
date: 2018-03-01
forum: Ubuntu Development Version
---

### Post by violetdsobieski on 2018-03-01
I have installed Ubuntu 16.06 on a 110Gb Partition, Ubuntu 18.04 on another 110Gb Partition and the rest is left over for SWAP on a 240Gb SSD. Grub Boot Loader for Ubuntu 18.04 is a mess of black and white test and when navigating through the boot options the text becomes warped and is almost not readable. The only solution I have is to reinstall grub from Ubuntu 16.04 which corrects the problem. I have tried reinstalling grub from Ubuntu 18.04 post all the updates but it is still a total mess.

---

### Post by VMC on 2018-03-01
Yes, I noticed it also on both lubuntu, and xubuntu. It must be how grub.cfg is configured. Once I use my own grub.cfg on the grub boot loader, the issue goes away.

---

### Post by flocculant on 2018-03-02
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1748028](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1748028)

Just pinged Steve Langasek on irc - they've now seen this bug elsewhere ( I just marked mine as a dupe to the one someone is assigned to fix it)

---

### Post by cecilpierce on 2018-03-02
Happens to me to, anyone get grub-emu to work ?

---

### Post by #&amp;thj^% on 2018-03-02
> **cecilpierce said:**
> Happens to me to, anyone get grub-emu to work ?

It works here, I just don't leave home without it. ;)
Grub Lives and looks as expected here. (Working)
If it matters, and i think not... I have Proposed enabled.
```
apt policy grub-emu
grub-emu:
  Installed: 2.02-2ubuntu7
  Candidate: 2.02-2ubuntu7
  Version table:
 *** 2.02-2ubuntu7 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by flocculant on 2018-03-03
> **violetdsobieski said:**
> I have installed Ubuntu 16.06 on a 110Gb Partition, Ubuntu 18.04 on another 110Gb Partition and the rest is left over for SWAP on a 240Gb SSD. Grub Boot Loader for Ubuntu 18.04 is a mess of black and white test and when navigating through the boot options the text becomes warped and is almost not readable. The only solution I have is to reinstall grub from Ubuntu 16.04 which corrects the problem. I have tried reinstalling grub from Ubuntu 18.04 post all the updates but it is still a total mess.

Edit /etc/grub.d/00_header to remove --append from the > terminal_output --append ${GRUB_TERMINAL_OUTPUT} line and then run update-grub

Grub will look fine then.

Eventually it'll get a fix - likely you'll be asked which version of the file you want to keep, the new one or your edited one - choose the new one and you'll be back using default grub files

---

### Post by cecilpierce on 2018-03-03
Thanks, that fixed the black on white flashing.

---

### Post by flocculant on 2018-03-05
bug is fixed now

---

### Post by Cavsfan on 2018-03-06
I was having the exact same problem when I installed it.
But, I immediately customized it and had no problem after that.

You could boot into 16.04 and enter **sudo grub-install /dev/sda/**  ("a' is assuming your 1st drive, or b for 2nd drive, etc.)

Then boot into 18.04 and enter **sudo dpkg-reconfigure grub-pc** or on efi systems **sudo dpkg-reconfigure grub-efi-amd64**
Just tab through the first few questions and then when it gets to the partition grub is installed on, remove the * from the MBR (Master Boot Record) e.g _sda_ or _sdb_, etc. 
Then place the * on the PBR (Partition Boot Record) e.g. _sda4_ or _sdb3_ etc..

It will whine about it a bit but, you won't have to worry about your grub moving from one system to the other everytime one gets an update. It will be on 16.04 until you change it.
Just remember where you put it.

This link [here]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#If_you_multiboot_mutiple_Linux_installs_and_want_one_Grub_to_control_all_of_your_OSs") will explain it a bit more.

---

