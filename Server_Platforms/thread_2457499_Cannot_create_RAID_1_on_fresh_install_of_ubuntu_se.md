---
title: "Cannot create RAID 1 on fresh install of ubuntu server 20.04"
date: 2021-02-03
forum: Server Platforms
---

### Post by alspector on 2021-02-03
I am moving back to Ubuntu server after about 8 years on FreeBSD and have two brand new drives on which I am trying to setup RAID 1. I seem to be stuck in a roundabout of a problem.

When I create the array using the disks unformated, I am able to create all file systems fine, however I am unable to proceed with the installation as I have not set the drives as boot devices and there is a message telling me as much at the top of the installer.

However, if I set the two drives as boot devices first, when I try to create the array, the two drives are not listed as available devices with which to create an array.

I used this post as a reference: [https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices](https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices)

Is there a way to work around this?

Thanks!

---

### Post by TheFu on 2021-02-03
If I wanted RAID1 for the OS, I'd do a normal install with LVM onto 1 disk, then post install, have LVM change to a RAID1 mirror.

It is almost always a bad idea to not lay down a partition table and at least 1 partition if using mdadm.  This provides some flexibility when it is time to replace a bad disk and the same model isn't available anymore.

Advanced storage setups with the installer has generally been lacking on ubuntu, though in 20.04, I do recall some access to controlling a few things that wasn't there previously. I recall because I cried with happiness in having just a little more control.  But it was about LVM, not mdadm that I noticed the improvements.  I just don't use mdadm except on legacy installs these days.

If you really want the setup that you want without lvm, you can do a manual install. I have no idea how. Debian has how-to guides.

---

### Post by slickymaster on 2021-02-04
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2021-02-04
I'd try to locate a third drive to use for the operating system.  Doesn't need to be all that big; 80 GB is plenty. Then I'd create partitions on both the RAID drives that span the entire disks and put them together with mdadm.

Alternatively you need to partition both drives with two partitions, a smaller partition for the operating system leaving the rest for RAID 1.  I have done this though it's a bit wasteful. You could put a second copy of the OS on the smaller partition of the second drive for backup/rescue.

---

### Post by darkod on 2021-02-04
To save time I would suggest to use the legacy server ISO instead of the now standard live server ISO.

Further more I would boot the server with the ubuntu desktop ISO in live mode first, prepare the disks (partitions), even maybe create the mdadm arrays that you need. After that when booting it with the legacy server ISO installer it will detect everything and you can install with ease.

You might see this as complicated but I am strong defender to plan and prepare your partitioning first, even before you fire up the installer. It gives you so much more control and you need to be in control of your server. Not to mention that since UEFI boot is around the partition layout you need on the disks got more complex. I really don't wanna leave that work to the installer. :)

After you have your server running, you could continue testing the live server ISO and see if you can find a solution and learn how to do it with the new installer. Myself I still haven't installed new server with the live server ISO.

---

