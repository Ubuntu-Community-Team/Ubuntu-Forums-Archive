---
title: "Uefi problem"
date: 2017-03-14
forum: Ubuntu Studio
---

### Post by lordm2 on 2017-03-14
Hello, I use Ubuntustudio by years and I just got a new Acer pc with win10 installed. I can't get rid of the proprietary system because I teach graphic design both with opensource and commercial software.
I had installed many linux versions around with no problem at all. But the new uefi system is bugging me.

I can manage to boot dvd or usb stick UbuntuStudio 16.04 LTS and start the installation but the install fails to install grub-efi-64 (or something like...)

Booting in legacy mode will not boot windows at all, is that normal? Do I have to install all in legacy and then switch back to secure boot?

I have a bit unclear all the installation tutorial. I followed step-by-step the one on ubuntu website and other websites but the result is the same. I stopped the legacy install because I have windows already setup with my software and I'd like to be sure to not loose the system.

Many thanks if you can clear me things out.

---

### Post by oldfred on 2017-03-14
What model Acer?
All Acer do have a unique requirement that once installed, you have to go into UEFI, see a UEFI supervisory password (never lose that or erase immediately after done) and enable "trust" from within UEFI on the ubuntu/grub .efi files in the ESP.

Also make sure you have newest UEFI from Acer.
Some said you had to downgrade UEFI, but newer threads mention newest works.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by lordm2 on 2017-03-22
Hello again,
after many tries it gives the same error 

"grub-efi-64-signed can't be installed in /target"

Under the part of hardware configuration. I will try ubuntu standard to see if there is any difference.

Things I did:

- Update BIOS
- Set superuser password
- Installation with and without secure boot
- rewritten the USB drive
- Signed as trusted the efi on the USB drive (that should be useless but just in case)

Nothing changes the installation, it can't be installed.

If anyone has ideas. Do I should put a screen of the error? Log is not so usefull

I would like to have Ubuntustudio for the artistic content, sure I can reconfigure a standard Ubuntu or pass to another distro and add PPA and stuff.
But with Ubuntustudio should be simpler.

Many thanks for the help

---

### Post by oldfred on 2017-03-22
Which partition is the ESP - efi system partition?
Post this:
sudo parted -l

Some just need to run chkdsk (if you also have Windows) or dosfsck on the ESP as it is FAT32.
Change example of sdb1 to your ESP.
 Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by lordm2 on 2017-03-23
Thanks for the reply.
Just for test I tried Ubuntu 16.04 and it installs smoothly without problems.

It seems that Ubuntustudio 16.04 has some bug in this installation system. I usually install just LTS editions, so now I think I will wait for the Ubuntustudio 17.04 and try again to see if the problem is fixed.

Many thanks for the help but there are too many work around, not that I can't understand or I am inexperienced user. I don't have just the time to fix this things and I will go with a working distro instead and waiting the one of my preference can work without troubles.

Just know that in acer e5-575g there is this installation problem.

---

