---
title: "Seems like ubuntu server deleted my user (after crash)"
date: 2012-04-08
forum: Server Platforms
---

### Post by Thekay85 on 2012-04-08
Hello! My server crashed a few days ago and i ran a fsck from a Ubuntu Live USB, now it boots but my user (called daniel) is gone and i can't login as root. Trying to reset the password for root when in rescue mode gives an error saying "authentication token manipulation error". 
The problem started when I ran a update, after that my mysql db stopped working so i rebooted and got:
```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```

Followed this guy [http://ubuntuforums.org/showthread.php?t=1726541](http://ubuntuforums.org/showthread.php?t=1726541) and I got it to boot and start the server but the users/passwords didn't work anymore.
At the moment Im cloning the system hard drive to another hard drive with ddrescue because im out of ideas and the system drive has "some" bad sectors according to disc utilty. It will be done in a few hours, but i can almost bet it wont do any difference.

Questions:
Is my installation doomed?
Why did my user disappear?

Regards
Daniel

---

### Post by darkod on 2012-04-08
Which part did you follow, all of it? He is talking about LVM, are you running LVM too?

As for the rest in his post, I don't agree with the read/write thing and that you can't do it from a cd. I don't see anything you couldn't do with chroot into your installation.

Even copying running from the cd should be OK as long as you copy to ext hdd (or course you can't copy to the cd).

---

### Post by Thekay85 on 2012-04-08
> **darkod said:**
> Which part did you follow, all of it? He is talking about LVM, are you running LVM too?

As for the rest in his post, I don't agree with the read/write thing and that you can't do it from a cd. I don't see anything you couldn't do with chroot into your installation.

Even copying running from the cd should be OK as long as you copy to ext hdd (or course you can't copy to the cd).

The last part with the lvm i did, and that got it to boot again. I used a usb with Ubuntu Live that i made in unetbootin with space for saving system settings. I haven't however copied anything from the drive since there is nothing to find on it except standard system files.

---

### Post by darkod on 2012-04-08
OK, try this. Boot again with the usb stick in live mode (not from the hdd), and in terminal try:
sudo apt-get install lvm2 (that will install it temporarily in the live mode)

To scan all disks for physical volumes:
sudo pvscan

To scan for volume groups:
sudo vgscan

Does it find all volume groups you had? How many does it find?

If you want to, you can continue with activating the volume groups with:
sudo vgchange -a y

And then scan for logical volumes with:
sudo lvscan

How many are there?

---

