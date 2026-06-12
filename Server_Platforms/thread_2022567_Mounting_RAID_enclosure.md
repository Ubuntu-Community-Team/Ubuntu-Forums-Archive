---
title: "Mounting RAID enclosure"
date: 2012-07-11
forum: Server Platforms
---

### Post by Frankincense93 on 2012-07-11
He guys I have finally bought 2 x 1TB HDDs for my sharkoon 5 bay RAID enclosure. I have put them into RAID 1 and everything good. I plugged it into my Windows PC first just to test it all worked, after a big of jiggling with loading a default hard disk driver and using Computer Management to create a partition I got it visible as a single HDD in Windows.

I now need to mount it on my Ubuntu server so I can start using it properly. Unfortunately after plugging it in I can't see anything in /media or /mnt (other than cddrive), running the mount command doesnt give anything obvious (I dont really know what Im looking at) and fdisk -l does return anything.

I was wondering if anyone had experience of this, might know what the problem is or just any bit of help would be greatly appreciated :)


Cheers,
Jack

---

### Post by darkod on 2012-07-11
First, how is it connected to the server? Ethernet? USB?

For the enclosure to work as a raid it might have some small linux based OS on it. And it would usually have ethernet connection.

If it's Ethernet, you would have configured it somehow with an IP on your local LAN (or it would receive it automatically with dhcp). So, you need to mount it using that IP and the share name(s) configured.

If it's USB, I guess it's down to drivers whether it's detected or not. I am not sure if it gives the same result as fdisk -l but you can also view all disks and partitions detected by:
cat /proc/partitions

---

### Post by Frankincense93 on 2012-07-11
It can be either USB3.0 or eSata. (Currently eSata).


The output of cat /proc/partitions is:

major minor  #blocks  name

   8        0  244198584 sda
   8        1     248832 sda1
   8        2          1 sda2
   8        5  243947520 sda5
   8       16  976715776 sdb
   8       17  976712704 sdb1
 252        0  241856512 dm-0
 252        1    2088960 dm-1

Im not sure what is what there tbh

---

### Post by darkod on 2012-07-11
> **Frankincense93 said:**
> It can be either USB3.0 or eSata. (Currently eSata).


The output of cat /proc/partitions is:

major minor  #blocks  name

   8        0  244198584 sda
   8        1     248832 sda1
   8        2          1 sda2
   8        5  243947520 sda5
   8       16  976715776 sdb
   8       17  976712704 sdb1
 252        0  241856512 dm-0
 252        1    2088960 dm-1

Im not sure what is what there tbh

OK, it looks like sdb. You can do a quick test. Did you create the partition on the array as ntfs? I assume, so you can access it from windows too.

If it is ntfs, try a temporary mount like:
sudo ntfs-3g /dev/sdb1 /mnt
ls /mnt

Does that list the folders/files on the array?

---

### Post by Frankincense93 on 2012-07-11
Yes it was ntfs.

Running 'sudo ntfs-3g /dev/sdb1 /mnt' outputs:
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

But mnt seems to be still empty, but currently there is nothing on the HDDs so im not sure what to expect

---

### Post by darkod on 2012-07-11
> **Frankincense93 said:**
> Yes it was ntfs.

Running 'sudo ntfs-3g /dev/sdb1 /mnt' outputs:
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

But mnt seems to be still empty, but currently there is nothing on the HDDs so im not sure what to expect

Well, looks like you found it.

I didn't think it was empty. If there is nothing on it, or course the ls will not show anything.

Also, when removing the device under windows, don't forget to always use the Eject procedure so that it closes it cleanly. The error shown was because of that.

You can do the following test, to be sure:
Connect it to your windows machine, copy something to it, eject it cleanly.
Connect it to the ubuntu server again, and do the above test. Now it should show the content with ls.

Otherwise, the permanent mount would be an entry in /etc/fstab something like:
```
/dev/sdb1   /moint-point   ntfs   defaults   0   0
```For the mount point you can call it as you want, but you have to create the folder first. Something like:
sudo mkdir /media/sharkoon

for example. In that case the mount point is /media/sharkoon.

Also, since it's removable device, to make sure you are always mounting the correct partition instead of /dev/sdb1 you can use:
UUID=<long UUID string>

You can view the UUID strings for each partition with:
sudo blkid

Those strings are unique and don't change unless you format the partition.

For example, if tomorrow you add another internal hdd in your server, when connecting the external it can become sdc (the internals will be sda and sdb). In this case your /dev/sdb1 entry in fstab will no longer be correct and it will not work. But if you used the UUID it will keep working without problems.

---

### Post by Frankincense93 on 2012-07-11
> **darkod said:**
> Well, looks like you found it.

I didn't think it was empty. If there is nothing on it, or course the ls will not show anything.

Also, when removing the device under windows, don't forget to always use the Eject procedure so that it closes it cleanly. The error shown was because of that.

You can do the following test, to be sure:
Connect it to your windows machine, copy something to it, eject it cleanly.
Connect it to the ubuntu server again, and do the above test. Now it should show the content with ls.

Otherwise, the permanent mount would be an entry in /etc/fstab something like:
```
/dev/sdb1   /moint-point   ntfs   defaults   0   0
```For the mount point you can call it as you want, but you have to create the folder first. Something like:
sudo mkdir /media/sharkoon

for example. In that case the mount point is /media/sharkoon.

Also, since it's removable device, to make sure you are always mounting the correct partition instead of /dev/sdb1 you can use:
UUID=<long UUID string>

You can view the UUID strings for each partition with:
sudo blkid

Those strings are unique and don't change unless you format the partition.

For example, if tomorrow you add another internal hdd in your server, when connecting the external it can become sdc (the internals will be sda and sdb). In this case your /dev/sdb1 entry in fstab will no longer be correct and it will not work. But if you used the UUID it will keep working without problems.


Fantastic help!

Using this aswell: [http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/](http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/)

I think I have managed to mount the drives in /media/RAID/.

Is there any way to test whether the drive is mounted properly and the information is being written to the RAID and not the normal HDD?

---

### Post by darkod on 2012-07-11
It shows all mounted partitions (except swap) with:
df -h

It should have a line like:
/dev/sdb1   total size   used etc   /media/RAID

That confirms at which mount point it's mounted.

Once you confirm that, writing to /media/RAID (or listing its contents) has to be the raid enclosure, no doubt.

With df -h it will also show the used percentage so you can keep an eye once in a while.

---

### Post by Frankincense93 on 2012-07-11
> **darkod said:**
> It shows all mounted partitions (except swap) with:
df -h

It should have a line like:
/dev/sdb1   total size   used etc   /media/RAID

That confirms at which mount point it's mounted.

Once you confirm that, writing to /media/RAID (or listing its contents) has to be the raid enclosure, no doubt.

With df -h it will also show the used percentage so you can keep an eye once in a while.

I can confirm it is mounted correctly :)

You my friend have been a fantastic help, thanks again!

---

### Post by darkod on 2012-07-11
No problem. You are welcome. :)

---

