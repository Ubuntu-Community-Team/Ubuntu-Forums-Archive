---
title: "move desktop to 2nd hard drive"
date: 2013-10-07
forum: Ubuntu Studio
---

### Post by ratpicker on 2013-10-07
i am running ubuntu studio 12.04 and have two hard drives installed, a 120 gb solid state drive and a 1 tb sata drive.  i recently realized my system was only using the 120 gb solid state drive when i ran out of storage space.  i want to use the solid state drive for the operating system and programs that need to be run when booting up and use the 1 tb sata for storage and to house the desktop folders, etc.  

i have formatted the sata drive and changed the permissions so i can write to it.  my question is ; how can i set ubuntu studio to automatically use it for file storage?

---

### Post by cub on 2013-10-07
So, if I have understood you correctly you want to 120 GB solid state to have the OS and save all your user data on the 1 TB sata drive? In that case you need to move /home to the sata drive. This should be helpful: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2013-10-07
Moving /home is one way to do it.
Another is to split /home and leave the user configuration files which are mostly the hidden files with dot as first character. All those files are tiny. But a few applications may also write data into /home like Firefox & Thunderbird. 

I have all data in two data partition in my hard drive and my Ubuntu install on my SSD (sde). One data partition is still NTFS from when I used to also boot XP, but I still have not reconfigured to not use NTFS.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde3        28G   11G   16G  42% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sdd2       100G   38G   63G  38% /mnt/shared
/dev/sdd6        97G   49G   43G  54% /mnt/data

```

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by ratpicker on 2013-10-07
thank you guys for your help.  i have been on microsoft forever with only limited linux experience.  i am now using ubuntu studio on all my machines and i am still feeling my way around.  i will give these things a try.  once i got the 1 bt drive formatted and the permission changed i was able to cut and past the larger folders from the sdd to the 1 tb drive and get the machine back working but moving or splitting home sounds like what i want to do.  i appreciate the help.

---

### Post by ratpicker on 2014-02-10
> **cub said:**
> So, if I have understood you correctly you want to 120 GB solid state to have the OS and save all your user data on the 1 TB sata drive? In that case you need to move /home to the sata drive. This should be helpful: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

just wanted to update my status.  

i followed the instructions in the link and succesfully moved my home directory.  now my machine still boots up quickly with the OS on the 120 gb ssd drive and all home directory stuff is automatically stored on the 1tb sata drive.  this is exactly what i was trying to accomplish.  thanks for the help.  

i love ubuntu and one reason is the support.  i have yet to spend hours on the phone with someone in a distant land telling me to reboot 40 times and yet all computing problems are easily resolved.

---

### Post by su:bhatta on 2014-02-10
Welcome to the world of Linux for creative humans

Please mark the thread as 'Solved' by using the 'Thread Tools' at the top right of the page that will help others too. :)

---

