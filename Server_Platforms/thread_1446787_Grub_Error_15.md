---
title: "Grub Error 15"
date: 2010-04-04
forum: Server Platforms
---

### Post by batty on 2010-04-04
I am trying to set-up a home server using Ubuntu 9.10 server edition.

My PC has 4 x 500Gb SATA drives which I will use for storage.

I also have a 80Gb IDE drive which I want to install OS on.

During installation the 80Gb IDE drive shows as sde.
When doing the install I chose to install to whole disk (sde), all appears to go well.

When I reboot all I get is "GRUB loading, please wait.... Error 15"

Is the problem caused by my drive being sde and not sda?
I have also tried partitioning sde as /. /boot and swap, still get Error 15.

Help!!

Dave

---

### Post by KB1JWQ on 2010-04-04
Common issue.

[http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/) may be enough to get you started.  If not, report back!

---

### Post by batty on 2010-04-05
I used a live CD to allow me to boot PC.
The page you directed me to says:

"You need to make changes to your /boot/grub/menu.lst file" 

I can find no such file on my PC. I think "menu.lst" is no longer used by the current version of Grub.

Dave

---

### Post by batty on 2010-04-05
Done a bit more searching on this subject,
Grub2 is now used in Ubuntu 9.10 so menu.lst no longer exists.

I booted up with my server installation CD and selected repair.
I then picked option to run a shell on my drive.

I then ran the command "grub-install /dev/sde" and now it works fine!

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Must remember to read all wiki articles first.

Thanks to everyone who keeps them up to date

Dave

---

