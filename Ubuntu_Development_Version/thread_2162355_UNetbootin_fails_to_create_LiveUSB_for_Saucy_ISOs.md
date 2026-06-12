---
title: "UNetbootin fails to create LiveUSB for Saucy ISOs"
date: 2013-07-14
forum: Ubuntu Development Version
---

### Post by amjjawad on 2013-07-14
Hi,

I am testing many Ubuntu Variants for this Cycle (Lubuntu, Xubuntu, Ubuntu-GNOME) and I can not create LiveUSB using UNetbootin, I have to do that using 'dd' because even the disk creator fails.

I have created this bug:
[https://bugs.launchpad.net/ubuntu/+bug/1201091](https://bugs.launchpad.net/ubuntu/+bug/1201091)

Am I the only one?

---

### Post by jerrylamos on 2013-07-14
I boot the development test iso's directly from the hard disk.
zsync the .iso and put it into the first directory of a partition.
Example below uses partition 6 on the boot hard drive
```
sudo gedit /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "saucy64 13.10" {
set isofile="/saucy-desktop-amd64.iso"
loopback loop (hd0,6)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
save
exit
sudo chmod 777 /etc/grub.d/40_custom
sudo update-grub
sudo grub-install /dev/sda            (whatever /dev/sd? you boot from)
sudo reboot
```
Faster for me than creating a USB. Of course, does not test the ability/inability of whatever you're using to create a USB.
Sometimes it's /casper/vmlinuz.efi and sometimes it's /casper/vmlinuz. With file manager select the .iso, which may allow you to browse the .iso to see which vmlinuz it is.

After rebooting, the grub entry you just made with 40_custom should be on the bottom.
Select & see if it boots....
Play with the live image if you wish.
Then
Ctrl-Alt-t
to get a terminal session
df
to see which /dev is the isodevice, no surprise in this case /dev/sdb6
sudo umount -rl /dev/sdb6                         (that's lower case RL)
exit the terminal session if you wish
open the install.

A bit long winded to read about after doing this a bunch of times I usually remember everything...
With test notebook, netbook, and desktop I'm installing every couple weeks - more lately playing with mir & unity8.  Conclusion: not ready for my level yet.

Note, I'm testing saucy on a USB hard drive, an SSD. 
The pc is set up to boot on the USB so during boot grub thinks the USB is /dev/sda
After boot, file manager, gparted, and install show it as /dev/sdb
Go figure.
BTW, if you intend to boot off a USB hard drive like I do, watch that install puts the boot image on /dev/sdb. Whatever your setup is.
Also you can have multiple 40_custom entries for multiple .iso's. Repeat and modify everything from menuentry to the final }

---

### Post by oldfred on 2013-07-14
I also directly boot ISO like jerrylamos.

But I only have a small configfile in my 40_custom, and then can edit the configfile at will without having to remember to run the sudo update-grub which I invariably forget to rerun. Then I have many ISO boot entries in configfile which are the same boot entries as I would have in 40_custom.

```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

I have found that boot drive from BIOS is always hd0 in grub. But other drives then are in port order from SATA ports on motherboard. And when I installed new drives I skipped a port and now if I plug in a flash drive it becomes that port, otherwise the next drive is that port. Or it can be confusing and which drive's MBR I boot from may change the configfile entry of  (hd2,4) to a different hd.

---

### Post by jerrylamos on 2013-07-14
> **oldfred said:**
> I have found that boot drive from BIOS is always hd0 in grub. But other drives then are in port order from SATA ports on motherboard. And when I installed new drives I skipped a port and now if I plug in a flash drive it becomes that port, otherwise the next drive is that port. Or it can be confusing and which drive's MBR I boot from may change the configfile entry of  (hd2,4) to a different hd.  My desktop has a sata drive and a ide drive.  Used to be no trouble with ubuntu, until about 12.04 where ubuntu can't figure out which is sda and which is sdb and which is hd0 and which is hd1 and changes which is which sometimes even during boot.  I've tried setting bios either way and ubuntu is still confused.  I used to just use 10.04 lucid to do update-grub grub-install since lucid can figure out what's going on.   however, with 10.04's grub the 13.xx's wind up with a horribly confusing grub entry and even duplicates.

Yeh, I entered launchpad bugs, nobody interested.

So I just put up with it.

---

### Post by pqwoerituytrueiwoq on 2013-07-14
i have a usb with grub on it 
on Ubutu and Ubuntu Gnome [FONT=courier new]/casper/vmlinuz[/FONT] does not exist but [FONT=courier new]/casper/vmlinuz.efi[/FONT] does (3ed line form the end of the code i posted)
grub.cfg:
```
set timeout=3
set default=0

menuentry "Xubuntu 13.10 Desktop ISO AMD64" {
 loopback loop /saucy-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/saucy-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}
```
start at step III
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

once you are done all you do is replace the iso to update it

i have a multiboot 32gb usb for stable releases

---

### Post by VinDSL on 2013-07-14
Glad I followed that bug.  Official PPA version is way behind.

```
vindsl@Zuul:~$ apt-cache policy unetbootin
unetbootin:
  Installed: 575-1ubuntu1
  Candidate: 575-1ubuntu1
  Version table:
 *** 575-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe i386 Packages
        100 /var/lib/dpkg/statu
```


Latest build: [585-1~saucy1]("https://launchpad.net/~gezakovacs/+archive/ppa")

---

### Post by sudodus on 2013-07-15
> **amjjawad said:**
> Hi,

I am testing many Ubuntu Variants for this Cycle (Lubuntu, Xubuntu, Ubuntu-GNOME) and I can not create LiveUSB using UNetbootin, I have to do that using 'dd' because even the disk creator fails.

I have created this bug:
[https://bugs.launchpad.net/ubuntu/+bug/1201091](https://bugs.launchpad.net/ubuntu/+bug/1201091)

Am I the only one?

Probably Unetbootin is not ready for Saucy.

The ***dd*** method has a high success rate provided there are no typing errors ;-) But the file system is read only, you won't get any persistence.

Will ***usb-creator-gtk*** work for you with the addition of two packages according to this link?

[http://ubuntuforums.org/showthread.php?t=1958073&p=12683981#post12683981](http://ubuntuforums.org/showthread.php?t=1958073&p=12683981#post12683981)

Or does ***usb-creator-kde*** work for you?

Please let me know your results with the usb-creator!

---

### Post by amjjawad on 2013-09-16
Hi,

The latest version of UNetbootin - [http://launchpad.net/~gezakovacs/+archive/ppa]("http://launchpad.net/%7Egezakovacs/+archive/ppa")
So far, works like a charm with 13.10 BUT I have not yet tested/tried that on 13.04 ISOs as of now.

Thanks!

---

