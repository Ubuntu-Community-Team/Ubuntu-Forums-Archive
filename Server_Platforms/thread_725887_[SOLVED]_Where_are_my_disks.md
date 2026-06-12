---
title: "[SOLVED] Where are my disks?"
date: 2008-03-16
forum: Server Platforms
---

### Post by Rmantingh on 2008-03-16
I have bought (rented) a dedicated server from a 3rd party ISP which has Ubuntu Dapper on it.

cat /etc/issue
Ubuntu 6.06.2 LTS

cat /proc/version
Linux version 2.6.22-8-server (buildd@palmer) (gcc version 4.1.3 20070629 (prerelease) (Ubuntu 4.1.2-13ubuntu2)) #1 SMP Thu Jul 12 16:28:57 GMT 2007

I have no physical access to this server or a GUI and am using SSH to find my way around the system.
My problem is that I do not have any swap space on this machine and I can't see any physical disks attached to the server. Could it be that disks are not physically connected to the machine but rather on the network? Would the server then boot from the network? I'm not very knowledgable with servers so any help would be appreciated.

My /etc/fstab is empty and the df command just comes back with an empty list.

How can I find out about my disk storage?

Even if the disks are in RAID I should be able to find something about the partitions on it?

If I do cat /proc/diskstats then I do see a list which mentions /dev/sda, /dev/sda1 and /dev/sda2 but if I do a fdisk /dev/sda it says Unable to open /dev/sda.

The reason I'm asking is because I want to install Oracle XE on the server and for some reason the installation fails and I was wondering whether it had anything to do with the machine having no swap space or some other system requirement not being met.

Thanks.

---

### Post by bigredradio on 2008-03-20
Sounds like a question for you provider. They may be using some sort of virtualization scheme, but I have not heard of one that does not at least mimic physical disks that you can partition or create filesystems. You might want to try 

# cat /proc/partitions

The fact that you cannot do a df is really strange. How will you know how much free space you have on the system? 

I would question whether this system have been compromised. You might have a rootkit on the system. The rootkit may have replaced basic commands that are not reporting correctly. If you proc entries are o.k., but commands give unexpected output, then check the mod dates on the commands and make sure you are running the correct df. ls -la `which df`. Also, compare an ls of /bin and /sbin with an echo * inside /bin and /sbin. You might see more files with the echo * than the ls. This is another tell tale sign. I might be paranoid, so start with your provider first. Maybe they have a simple explanation.

---

### Post by Rmantingh on 2008-03-20
Thanks for the information.
I would ask my hosting provider but they (123-reg) are probably the worst on the planet for customer service :-(

$ ls -la `which df`
-rwxr-xr-x 1 root root 34524 2006-05-05 18:50 /bin/df

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on

$ mount -l
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)

$ cat /proc/partitions
major minor  #blocks  name

   8     0  156250000 sda
   8     1    2104514 sda1
   8     2  154143675 sda2

So there's definitely something there.

$ du -s /*
20	/admin
4628	/bin
104	/boot
8	/dev
5628	/domains
8820	/etc
0	/frontpage
8	/fs
210900	/home
4	/initrd
11348	/lib
4	/media
4	/mnt
7765352	/opt
0	/proc
1804	/root
7232	/sbin
4	/srv
0	/sys
24	/tmp
572200	/usr
92124	/var

I've also found out that it may be possible to create a swap area in a file instead of partition so I may look into that next.
In the mean time I have been able to install the standard Oracle 11g database on the machine (which allows you to ignore system requirements such as sufficient swap) but if I want to use that I will need a license which I want to avoid.

Thanks anyway for looking into this.

---

### Post by Rmantingh on 2008-03-29
For posterity....
I found the solution. My system is indeed a virtual chroot-jailed system.
I found a way to break out of that.
[http://ubuntuforums.org/showthread.php?t=723132&highlight=123-reg](http://ubuntuforums.org/showthread.php?t=723132&highlight=123-reg) (post #9)

---

