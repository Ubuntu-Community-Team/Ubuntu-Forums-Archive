---
title: "If Xenial on 2nd Drive in Debian Box, Will Grub Offer Both?"
date: 2015-10-24
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2015-10-24
I'm thinking of putting Xenial on the currently unused second drive in a machine that boots Debian on the first drive, once iso's are available.

If I opt for "Something Else" and point the partitioner at the second drive, which Grub -- Debian's or Ubuntu's -- will be used after that and will it automagically offer a dualboot choice of Debian or Ubuntu?

---

### Post by ronacc on 2015-10-24
short answer  yes , a little longer answer ,depends on where you have xenial ( or any 2nd 0r 3rd  install ) put its grub you may need to run this command in a terminal  when booted into the first install .  > sudo update-grub< .  I have a multi boot box with 7 installs ( varies from week to week ) all booting from the install on SDA .

---

### Post by grahammechanical on 2015-10-24
The Ubuntu installer defaults to installing Grub into the MBR of sda. You do not want that if Ubuntu is to be on sdb. Underneath the panel that lists the partitions there is another panel where we can select where to install Grub. It is useful to be able to use the BIOS to select which hard drive to boot from.

I assume that Debian uses Grub. So, if Debian is installed last and its Grub is installed in sda then boot from sda and you will have an option to load Ubuntu. Once in Ubuntu run this command

```
sudo update-grub
```

and then the Ubuntu Grub will detect the Debian install. Then it should not matter whether you boot from sda or sdb you should get an option to load either Debian or Ubuntu. Remember, If Ubuntu upgrades the kernel the Debian Grub will not know about it unless you run that command from Debian. And the same thing happens if it is Debian that gets the kernel upgrade.

I have never installed Debian. So, I am making some assumptions about the way Debian does things. Ubuntu uses a script called update-grub. It runs grub-mkconfig. Debian might not use that script. You might have to run grub-mkconfig directly. This is the contents of Ubuntu's update-grub script.

> #!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

Regards.

---

### Post by ronacc on 2015-10-24
a handy thing to have on hand incase you have an oops is a copy of super grub2 disk , it can repair a fouled up grub , you can get it here > [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) < . burn it to a cd and keep it handy .

---

### Post by buzzingrobot on 2015-10-24
OK, thanks all.  Looks like I can put Ubuntu on /dev/sdb, tell the installer to put its bootloader on '/' there, leave the BIOS set to boot from Debian on /dev/sda, then run Debian's update-grub (same script as Ubuntu) and it will run os-prober to probe for other OS's, then reconfigure Debian's grub and its menu to include the Ubuntu install. Then I keep an eye out for Xenial kernel updates.

I guess I might know something about this if I'd ever dual-booted Windows. I usually jump on the development release somewhere mid-course, but since I've got this drive available now, I'll use it. I see the mini.iso is at archive.ubuntu.com.  If memory serves, that has the option to install any of the full desktops, but I think I'll wait for the regular install images to arrive.

[EDIT:  SuperGrub2Disk acquired.  Nice tip.]

---

### Post by ronacc on 2015-10-24
if you are only going to put one install on sdb have ubuntu put its grub in the MBR on sdb and you will be able to switch boot drives in bios incase sda encounters a problem and boot from sdb .  that way you have a built in backup .

---

