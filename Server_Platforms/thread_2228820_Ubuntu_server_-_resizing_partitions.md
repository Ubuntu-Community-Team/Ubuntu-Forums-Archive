---
title: "Ubuntu server - resizing partitions"
date: 2014-06-09
forum: Server Platforms
---

### Post by szlapy on 2014-06-09
Hello there,
Some time ago I set up an ubuntu server 13.10 and being little naive I used 8GB usb drive. It started with a samba server to share disk space for few windows machines at home. Soon I added a cups server for printer sharing and a sane server for scanner sharing. Then added serviio and subsonic. All was good for few weeks and then the whole thing slowed down. I realised I'm running out of space. Since all was working I uninstalled webmin and gained some space so that now all works, but I do not expect this to last long. Anyway I clonned the system to a 32GB usb drive, but it works still as the previous 8GB drive. Now I want to resize partitions to benefit from all the space I have on the usb drive. 

This is what I get when I run df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       2.3G  1.9G  209M  91% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           787M  2.0M  785M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G     0  3.9G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdd6       4.7G   66M  4.4G   2% /home
/dev/sda1       2.7T  519G  2.1T  20% /mnt/disk1
/dev/sdb1       1.8T  541G  1.2T  32% /mnt/disk2
/dev/sdc1       187G   16G  163G   9% /mnt/disk3

The last three mounts are my disks shared via samba all above these sits in the 32GB usb drive. 

I took the usb drive and used GParted in another computer to resize the partitions, but it didn't work. Then I searched internet and learnt that my approach was wrong and couldn't work. I cloned the 8GB drive afresh to this 32GB and tried to find a solution, but I couldn't find anything that would match my problem. Any suggestions? How can I approch this?
Thanks,
Piotr

---

### Post by oldfred on 2014-06-10
Why would gparted not work? But you could not have both flash drives connected at the same time as you would have duplicate UUIDs. You can change UUID, update fstab & reinstall grub if necessary.

You should be able to move/resize partitions. Of course their is always some risk in moving partitions as any interruption will corrupt partition.

Flash drives do not last as long as hard drives. If you have the hard drives why not install to one or more of them?

I like this logic on an install on every drive:
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Gyokuro on 2014-06-10
By that amount of hard drive space I'm always wondering why people do not use a LVM setup - it's flexible, save and clever as it's works somehow as a buffer so that disk do not get hit that hard with a lot of data. However to come back to the original problem I would move to content of your usb to the drive which hosts your /home directory but this is tricky and you should be fit with the commands and a good backup is a must. Most of the tips which you got already from oldfred should help you but I have search for an easy tutorial and here is one which should help you: [http://www.ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition-](http://www.ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition-) HTH

---

### Post by szlapy on 2014-06-10
Thanks oldfred and Gyokuro,

Answering the question why would gparted not work I found posts saying that it does not handle well ext3 partitions. Not sure why, but it didn't work when I tried. I prefer the system to be separated from data in the shared drives and with only 4 sata ports o the motherboards having the system on a usb stick seems to work very well. The only problem is the space allocated for the partitions. This must be solved.

Gyokuro, all these sit on the same physical usb stick:
/dev/sdd1       2.3G  1.9G  209M  91% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           787M  2.0M  785M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G     0  3.9G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdd6       4.7G   66M  4.4G   2% /home

I'll check the tutorial from Gyokuro and the sugestions from oldfred.
Cheers,
Piotr

---

