---
title: "Install Ubuntu server 10.04 from iso with grub2?"
date: 2011-12-14
forum: Server Platforms
---

### Post by H.S. on 2011-12-14
Hi all

It possible, with grub2, with option loopback, install from hdd, ubuntu server 10.04?

or, unzip iso file ubuntuserver 10.04, saved in the folder, and launch install
from folder with grub2?

Thanks :)

Regards:guitar:

---

### Post by arrrghhh on 2011-12-14
Why don't you just install from a USB key...?  I assume you're trying to get around the "need" for a CD drive?

I'm not sure if this is possible.  I would recommend USB key or PxE.  Hell, you can even install it on another system then move the HDD.  Just would have to change a few things related to the NIC as far as I know.

Good luck.

---

### Post by Habitual on 2011-12-14
[http://bobpeers.com/linux/hard_drive_install](http://bobpeers.com/linux/hard_drive_install) may have methods for doing this.
It specifically mentions Fedora, but the process should still work well enough for Ubuntu.

YMMV.

---

### Post by oldfred on 2011-12-14
Not sure if server version can be done the same or not:

Hard drive:
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it should have to be different partition or
sudo umount -lrf /isodevice
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by H.S. on 2011-12-16
Hi all

Thanks for all, but, for the version Server, this
method, function? :( 


Regards:guitar:

---

### Post by arrrghhh on 2011-12-16
> **H.S. said:**
> Hi all

Thanks for all, but, for the version Server, this
method, function? :( 


Regards:guitar:

I don't get the question.  The version shouldn't matter, this concept would work for any Linux install (I would imagine).  Just apply to concept to whatever distro you want to use.

---

### Post by H.S. on 2011-12-16
I mean that, the Server version, is not livecd.

Do you have any example for the version not livecd? :confused:

Thanks :)

Regards:guitar:

---

### Post by arrrghhh on 2011-12-16
> **H.S. said:**
> I mean that, the Server version, is not livecd.

Do you have any example for the version not livecd? :confused:

Thanks :)

Regards:guitar:

None of the examples provided explicitly require/use the LiveCD...

---

### Post by calarndt on 2013-01-22
Ok Lets get back to the initial topic. Which was, booting the server cd iso with grub 2.
The original posters question has gone unanswered here.

The problem:
GRUB2 understands and does know how to find the kernel via a loopback device.
However the initrd.gz that is included in the cd does apparently not understand how to find the install media.

Take this menuentry for example...

menuentry "Ubuntu 12.04.1 Server AMD64 ISO" {
 loopback loop /ubuntu-12.04.1-server-amd64.iso
 linux (loop)/install/vmlinuz iso-scan/filename=/ubuntu-12.04.1-server-amd64.iso noeject noprompt splash --
 initrd (loop)/install/initrd.gz
}
 
This does in fact boot the kernel and load the initrd. What happens though is that the installer borks at finding the cdrom ...  On my system it only looks at /dev/sr0 and dev sda and /dev/sda1... Consequently it does not actually work... There are several work arounds out there. Notably I just [ctrl-F2] mount the f lash and then mount the iso (loop) on /cdrom and then continue with the installer.

ISSUES are these:

1) Its only a work-around!
2) there are timing issues with the installer and doing it to soon results in the installer undoing the mounts you just did thereby requiring the lovely redo-it-all-again maddness.

So we still have a bunch of work to do...

Calvin

---

