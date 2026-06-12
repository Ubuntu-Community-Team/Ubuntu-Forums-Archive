---
title: "Best way to back up an Ubuntu Server install to USB?"
date: 2014-06-20
forum: Server Platforms
---

### Post by da2357 on 2014-06-20
Hello. I have Ubuntu Server 14.04 LTS installed and working fine on an 8GB USB flash-drive. Now that I've got it working fine, I'd like to be able to back it up so I can install the exact same configuration onto other USB flash-drives.

What's the best method for doing this?

---

### Post by sudodus on 2014-06-20
I would use ***Clonezilla*** and make an image of the whole source pendrive.

Then, to restore, you need a ***target drive of the same or bigger size***. USB pendrives are not exactly 8 GB, they can be 7.8 GB or something else, different from drive to drive, so to be sure it works, you must either check carefully the exact sizes of the source and target pendrives, for example with

```
sudo fdisk -lu
```

or use a 16 GB pendrive as target.

Test that restore really works (to another pendrive). Do not rely on the backup before it is tested!

---

### Post by papibe on 2014-06-20
Hi da2357.

I would make an image of the USB stick. You can use Partimage, or the command line 'dd'. Here's a good starting [tutorial]("https://help.ubuntu.com/community/DriveImaging").

[Clonezilla]("http://clonezilla.org/") also could be a alternative.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by tgalati4 on 2014-06-20
You can use the simple *cp* command.

Assuming the devices are the same size and located at /dev/sdg and /dev/sdh:  sudo cp /dev/sdg /dev/sdh

Understand that the Block ID's of the drives will be different (*blkid*) so they won't boot without UUID changes to /etc/fstab and grub2.

> 
tgalati4@Mint14-Extensa ~ $ grep UUID /etc/fstab
# device; this may be used with UUID= as a more robust way to name devices
UUID=b9e5433e-791c-4c7a-b08c-62f6820a474f /               ext4    errors=remount-ro 0      

tgalati4@Mint14-Extensa /boot/grub $ grep UUID grub.cfg
	linux	/boot/vmlinuz-3.5.0-48-generic root=UUID=b9e5433e-791c-4c7a-b08c-62f6820a474f ro   quiet splash $vt_handoff
	linux	/boot/vmlinuz-3.5.0-48-generic root=UUID=b9e5433e-791c-4c7a-b08c-62f6820a474f ro recovery nomodeset


The UUID must match the drive that the operating system is installed to.  There may be a script to automate this procedure, but you will have to search for it.

---

