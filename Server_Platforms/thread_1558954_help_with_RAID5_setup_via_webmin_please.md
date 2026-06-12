---
title: "help with RAID5 setup via webmin please"
date: 2010-08-22
forum: Server Platforms
---

### Post by sjhupp on 2010-08-22
Hi, have set up a server with OS on a 250GB disk (sdd) and 3x 1.5TB drives for a RAID5 storage setup (sda, sdb and sdc).
Using webmin I can delete and create a primary partition in each one.  But while I can also format sda and sdc, it refuses to do sdb for some reason:
Executing command mkfs -t ext4 /dev/sdb1 ; partprobe ..

mke2fs 1.41.11 (14-Mar-2010)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!

But I'm not using it
simon@ubuntu:~$ lsof | grep /dev/sdb
simon@ubuntu:~$ lsof | grep /dev/sdb1
simon@ubuntu:~$ fuser -m /dev/sdb
simon@ubuntu:~$ fuser -m /dev/sdb1
simon@ubuntu:~$ sudo umount -f -l /dev/sdb
umount: /dev/sdb: not mounted
simon@ubuntu:~$ sudo umount -f -l /dev/sdb1
umount: /dev/sdb1: not mounted

I can delete the sdb1 partition fine, but get the same error when I try to create it again!

Gparted gives the same error message.

Dumbfounded, please help?? :mad:

---

### Post by sjhupp on 2010-08-23
Ok, some progress.
After reading heaps of other posts, someone said removing mdadm enabled them to format their drive (similar situation to me, just 4 drives, one in use mysteriously).
So apt-get remove mdadm and reboot.
loaded webmin and formatted drive no probs! Yay!
then sudo apt-get install mdadm and reboot
loaded webmin to create RAID5 array... Error:

Then tried again to remove partition and the mdadm, reboot, and only use gparted to format the drive to ext4.
Success!!!  Rebooted, still there and ok.  Used webmin to flag as linux raid and rebooted - still all ok.
Finally installed mdadm again, and rebooted.
Then once more, webmin to create RAID5, and finally it worked!
Gave an error afterwards, but assumed because it wasn't mounted (no file system).
Anyway, formatted the md0 disk and away we go.
Hope this helps someone

---

### Post by Godsbrother on 2010-08-24
Im just trying this to see if it helps me setup a radi 5 array from 3 1tb disks...

I have been having huge problems trying to get it to create and stay through a reboot..

---

### Post by arrrghhh on 2010-08-24
I don't think Webmin is a very good way to setup a RAID array... Just because then you don't really know how it's setup.

But, if it works for you then it works for you... just look to Webmin for support :P

---

### Post by Godsbrother on 2010-08-24
I dont doubt you are correct it doesn't want to play ball at all. Just not al that familiar with doing it from the cmd line... spose now is as good a time as any to work it out!

---

### Post by Godsbrother on 2010-08-24
ok why is this failing?


sudo mdadm --create --verbose /dev/md0 --level=5 \ --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

mdadm: no raid-disks specified

---

### Post by arrrghhh on 2010-08-24
Please see [this](http://ubuntuforums.org/showthread.php?t=408461) how-to thread.

---

### Post by sjhupp on 2010-08-25
I admit I got scared when faced with the command line and avoiding wiping my install on sdd, and a couple howtos I found both followed webmin, as it was easy (supposedly). I must say webmin seemed ok, just mdadm appears in my case to somehow prevent me from creating the RAID5 config when installed.
I've since had files go on & off no probs, but I did have to chmod 777 the drive (I know, not secure, but a local home storage drive only) as webmin didn't appear to set any write permissions correctly.
I've looked at ebox as an alternative, but seems not quite 10.04 ready.

---

### Post by Godsbrother on 2010-08-25
> **arrrghhh said:**
> Please see [this](http://ubuntuforums.org/showthread.php?t=408461) how-to thread.

no help still fails with the same message

---

### Post by Godsbrother on 2010-08-25
ok looks like the cmd was at fault

sudo mdadm --create --verbose /dev/md0 --level=5 \ --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

I took out the \ after --level=5 and the cmd completed. However it instantly shows as recovering using

cat /proc/mdstat

something really doesn't like me! I have let it continue recovery after which I'm going to do some tests. If it isn't stable I think I will just call it quits and switch to fakeraid on another mobo.... not happy

---

### Post by sjhupp on 2010-08-25
FWIW, I now agree not to use webmin for RAID setup - raid won't mount on boot, si I get the fsck freeze on boot (needing to connect a keybord and hit 'S' to skip it).
Will be burning a live CD and doing that way.
Don't get why I can do from within the OS though (OS on a separate drive) but always get arrors with mdadm line above.

---

### Post by Godsbrother on 2010-08-26
> **sjhupp said:**
> FWIW, I now agree not to use webmin for RAID setup - raid won't mount on boot, si I get the fsck freeze on boot (needing to connect a keybord and hit 'S' to skip it).
Will be burning a live CD and doing that way.
Don't get why I can do from within the OS though (OS on a separate drive) but always get arrors with mdadm line above.

So youre going to use a live cd instead of booting into an existing Ubuntu install then setup the array?

hmm let us know if that works...

---

