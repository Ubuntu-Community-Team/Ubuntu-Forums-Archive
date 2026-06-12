---
title: "KVM Audio CD's and USB support"
date: 2009-12-27
forum: Virtualisation
---

### Post by ServerStorm on 2009-12-27
Hi everyone,

For the first time I have setup KVM on Ubuntu Karmic Koala 9.10 and have installed XP Pro as my first virtual machine. I have a problem where the XP Pro can not see an audio cd. Furthermore, to see a cd-rom I must first mount it in Ubuntu and then boot the XP Pro image using virt-manager - I then see the cd-rom, but if I eject the CD-ROM and try to load an audio cd, I see the audio cd in ubuntu but it does not load/mount in XP. 

If in Virtual Manager and a Add a CD source it again only sees a cd-rom source; with a audio cd the source is blank.

Is there a way to get my virtualized XP Pro to see audio cd's?

The whole reason for trying KVM is my daughter got an ipod touch for Christmas and I needed to install itunes under Windoze. I know that itunes can be installed in Linux but there are major problems with syncing and having to use multiple apps. My daughter is 10 she does not need this type of complication.

I have read that usb support has to be enabled in your virtual machine and that you have to set the proper usb signature for each usb device.

Can anyone walk me through how, using virsh, kvm, qmeu or virtual manager add usb and audio cd support for the xp pro virtual image?

Here are some details:

fstab:```
UUID=40e7fcaf-f87d-4361-9882-7a522cb9e942 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
```and listing CD-ROM devices:```
root@Serverstorn:/etc/libvirt/qemu# sudo ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 2009-12-26 14:32 /dev/cdrom2 -> sr0
lrwxrwxrwx 1 root root 3 2009-12-26 14:32 /dev/cdrw2 -> sr0

```I had also tried this under virtualbox although itunes locked up any time I tried to convert a CD and was very slow, which is why I tried KVM.

Your help is most appreciated.
Steve

---

