---
title: "Android x86 grub not loading in Virtualbox"
date: 2017-04-07
forum: Virtualisation
---

### Post by Hari5g900 on 2017-04-07
I tried installing Android x86 following the instructions [here]("https://www.howtogeek.com/164570/how-to-install-android-in-virtualbox/").
I figured the installation would be same in Windows and Ubuntu. I did make a better machine than the one specified and the installation went smoothly. But after the prompted restart, the machine fails to boot from hard drive. If I remove the disk image, the 'no bootable image found' error occurs.I think this is an issue of grub not loading properly? I have a Windows XP installation on a similar virtual machine and it loads up fine.

---

### Post by lammert-nijhof on 2017-04-07
The no boot image error is caused by your removal of the disk image. What does it mean; "the machine fails to boot from hard drive". What did happen, we need error messages and other observations to be able to help you. Did you remove the ISO image from the CD/DVD?

---

### Post by Hari5g900 on 2017-04-10
I had already installed the os to the "virtual" harddrive before i removed the iso. After installation it does not boot from the "virtual" harddrive instead shows the error.

---

### Post by Hari5g900 on 2017-04-28
Anybody have any ideas? I've still not found a solution to this problem.

---

