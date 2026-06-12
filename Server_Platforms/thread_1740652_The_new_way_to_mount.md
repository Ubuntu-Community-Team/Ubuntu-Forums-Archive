---
title: "The new way to mount"
date: 2011-04-27
forum: Server Platforms
---

### Post by fulldecent on 2011-04-27
Hello all,

I am used to mounting disks with 
```
mkdir -p /media/disk && mount -text3 /dev/sdc1 /media/disk
```

However, there's a few disadvantages to this:
* It takes two commands
* I have to know where I want to mount (I don't benefit from the disk label)
* The type needs to be known
* If I want to use a shorter command, I must edit fstab, and still know the two prior pieces of information
* Between restarts, the disk devices might change, wrecking my whole plan

Is there a better way to do this now from the command line? Also, what is the best way to mount/unmount disks from a script? Can I add the UUID to fstab?

Thank you,
Will

---

### Post by Lars Noodén on 2011-04-27
> **fulldecent said:**
>  Can I add the UUID to fstab?l

Yes, you can.  [blkid](http://manpages.ubuntu.com/manpages/natty/en/man8/blkid.8.html) will show the UUID of your device.

---

### Post by dtfinch on 2011-04-27
You can mount by label with -L. Like "mount -t ext3 -L disklabelhere /media/disk"

---

### Post by nebileix on 2011-04-27
U can try gnome-mount

---

### Post by elico on 2011-04-27
if you do need a "restart proof" mount use UUID.
i will five you a nice line for it from fstab:
> UUID=dxxeaxxx-xxxx-xxxx-xxxx-316efd11e719 /mnt/disk1/               ext4    errors=remount-ro 1       2

will mount specific drive that every restart will remain the same
as for replacing the two commands..
a label indeed most of the time is useless.
how many disks are you using?
you can create 10 dirs in the /mnt or /media directories and it's more then you will most likely ever need for disk on a desktop.

as fot the 
> -text3
what version of ubuntu are you using?
the last time i needed to use it was never...

so i hope this will help you.

---

### Post by arrrghhh on 2011-04-27
I am going to +1 the suggestion above - use the UUID, and use fstab.  Assuming the mounts aren't changing daily, fstab will take care of all the mounting tasks for you ;).

---

### Post by dtfinch on 2011-04-27
I've had reliability issues keeping external usb hard drives mounted for months at a time in fstab. We have some fire-proof external drives for secondary backups. After a while it would lose access to the external drive for various reasons, but it would still show as mounted, and we had silent failures for a while (a messaging script broke around the same time). Now in my backup script, I mount before the backup, and verify that mounting succeeded (to avoid writing to the root filesystem on failure), then sync and unmount when the backup is done. There's also an issue where it'll stop seeing the device at all after a while (maybe the drive goes to sleep), and my script needs to call lsusb, then sleep for a few seconds and call lsusb again before it'll be able to access the drive again, [as documented here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/645211).

---

### Post by fulldecent on 2011-04-28
Thank you all, I will investigate these, starting with the UUID method

---

### Post by elico on 2011-04-28
to [dtfinch]("http://ubuntuforums.org/member.php?u=8053")
i assume you have checked the log files and got nothing?
you can try to disable acpi option on the kernel by appending the kernel boot line on grub
> acpi = off
and if it is a power management problem it will most likely will fix it.

---

