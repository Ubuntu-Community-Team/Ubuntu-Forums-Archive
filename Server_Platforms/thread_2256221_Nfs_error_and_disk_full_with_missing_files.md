---
title: "Nfs error and disk full with missing files"
date: 2014-12-10
forum: Server Platforms
---

### Post by n-corvini on 2014-12-10
Hi, today i started a copy on an hdd (sdb) of my ubuntu server (14.04)via nfs from a client, after a few hours (1.5TB of files) the server send an error because the disk was full.
In teory this woud be impossible because the HD where the files were copied was a 3TB so I checked and the resoult was that the files werent copied to the correct hd but istead on the main hd (sda).
I checked /etc/exports and the entry was correct 
/home/3tb/      192.168.2.106(sync,no_subtree_check,no_root_squash,rw)
fstab:
UUID=f2ebae2f-499b-4c5d-8a04-fd5adf3940a9  /home/3tb   auto    rw,user,auto    0    0
after a reboot the nfs exports where all ok but all the files i had copied was missing but the hd space was not free.


i had tried:
-sudo find / -type f -size +100000k
but the files wasn't there, so i had tried: 
-sudo find / -name Anime   (Anime was one of the folders missing)
 with no results


-sudo df -h
File system                            Dim. Usati Dispon. Uso% Montato su
/dev/mapper/Cerberus--Server--vg-root  912G  865G    739M 100% /
none                                   4,0K     0    4,0K   0% /sys/fs/cgroup
udev                                   2,5G   12K    2,5G   1% /dev
tmpfs                                  497M  876K    496M   1% /run
none                                   5,0M     0    5,0M   0% /run/lock
none                                   2,5G  4,0K    2,5G   1% /run/shm
none                                   100M     0    100M   0% /run/user
/dev/sda1                              236M   75M    149M  34% /boot
/dev/sdb1                              2,7T   73M    2,6T   1% /home/3tb
/home/nico/.Private                    912G  865G    739M 100% /home/nico


-du -sh /home/
261G    /home/

-sudo du -sh /
du: impossibile accedere a "/proc/5200/task/5200/fd/4": File o directory non esistente
du: impossibile accedere a "/proc/5200/task/5200/fdinfo/4": File o directory non esistente
du: impossibile accedere a "/proc/5200/fd/4": File o directory non esistente
du: impossibile accedere a "/proc/5200/fdinfo/4": File o directory non esistente
265G    /

the files shoud be around 550GB

Any ideas how to find the files or remove them?
Thanks for the help

---

### Post by papibe on 2014-12-10
Hi n-corvini. Welcome to the forum ):P

May be the data is under home and the mount of the '3tb' disk is not letting you see the files. 

I would first try to umount the '3tb' disk to see if the data is down the /home folder.

If that's not possible, I would boot into recovery mode, get a root prompt and since there youwon't be mounting anything than the root filesystem, you would be able to look for the files.

Just a thought. Hope it helps.

Let us know how it goes.
Regards.

---

### Post by TheFu on 2014-12-10
Papibe nailed the issue perfectly.  The NFS mounted storage is "over" the previously copied files.  For any automatic tasks which copy to sometimes-mounted storage, it is best to verify the storage is mounted BEFORE doing a copy.

Oh - and we've all learned this the same way you are now learning it.  It is a neat trick to hide things sometimes too, so put this technique into the back of your mind for later. ;)

---

### Post by n-corvini on 2014-12-10
Thanks for the fast reply!
Umount seems not to work but you were right!
I have started in recovery mode and the missing dir was in a folder called in the same way that the 3tb!
Now I just have to move to another folder and is done.
Thanks a lot!

---

### Post by n-corvini on 2014-12-10
> **TheFu said:**
> Papibe nailed the issue perfectly.  The NFS mounted storage is "over" the previously copied files.  For any automatic tasks which copy to sometimes-mounted storage, it is best to verify the storage is mounted BEFORE doing a copy.

Oh - and we've all learned this the same way you are now learning it.  It is a neat trick to hide things sometimes too, so put this technique into the back of your mind for later. ;)

Thanks fore the hint ;)

---

