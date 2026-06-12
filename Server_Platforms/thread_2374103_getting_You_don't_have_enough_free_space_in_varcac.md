---
title: "getting You don't have enough free space in /var/cache/apt/archives/."
date: 2017-10-12
forum: Server Platforms
---

### Post by kustomjs on 2017-10-12
Hello Guys
I am currently getting this error code: You don't have enough free space in /var/cache/apt/archives/.     on my ubuntu server 16.04 lts and I have tried sudo apt-get autoremove and sudo autoremove still get that error code.

so I did this df -ha and got this:
```
Filesystem                 Size  Used Avail Use% Mounted on
sysfs                         0     0     0    - /sys
proc                          0     0     0    - /proc
udev                       2.0G     0  2.0G   0% /dev
devpts                        0     0     0    - /dev/pts
tmpfs                      396M   11M  385M   3% /run
/dev/mapper/mail--vg-root  455G  454G     0 100% /
securityfs                    0     0     0    - /sys/kernel/security
tmpfs                      2.0G     0  2.0G   0% /dev/shm
tmpfs                      5.0M     0  5.0M   0% /run/lock
tmpfs                      2.0G     0  2.0G   0% /sys/fs/cgroup
cgroup                        0     0     0    - /sys/fs/cgroup/systemd
pstore                        0     0     0    - /sys/fs/pstore
cgroup                        0     0     0    - /sys/fs/cgroup/devices
cgroup                        0     0     0    - /sys/fs/cgroup/cpu,cpuacct
cgroup                        0     0     0    - /sys/fs/cgroup/net_cls,net_prio
cgroup                        0     0     0    - /sys/fs/cgroup/cpuset
cgroup                        0     0     0    - /sys/fs/cgroup/memory
cgroup                        0     0     0    - /sys/fs/cgroup/pids
cgroup                        0     0     0    - /sys/fs/cgroup/blkio
cgroup                        0     0     0    - /sys/fs/cgroup/hugetlb
cgroup                        0     0     0    - /sys/fs/cgroup/perf_event
cgroup                        0     0     0    - /sys/fs/cgroup/freezer
systemd-1                     -     -     -    - /proc/sys/fs/binfmt_misc
mqueue                        0     0     0    - /dev/mqueue
hugetlbfs                     0     0     0    - /dev/hugepages
debugfs                       0     0     0    - /sys/kernel/debug
fusectl                       0     0     0    - /sys/fs/fuse/connections
/dev/vda1                  472M  467M     0 100% /boot
lxcfs                         0     0     0    - /var/lib/lxcfs
binfmt_misc                   0     0     0    - /proc/sys/fs/binfmt_misc
tracefs                       -     -     -    - /sys/kernel/debug/tracing
tmpfs                      396M     0  396M   0% /run/user/1000 
```

what can I do get it back to running mail server?

---

### Post by darkod on 2017-10-12
Both your root and /boot are 100% full. You need to free space. For /boot you can uninstall old kernels using dpkg. For root you need to delete some data to free up space.

---

### Post by deadflowr on 2017-10-12
```
sudo apt-get clean
```
clears out the archive, entirely.

Bonus is
```
sudo apt-get autoclean
```
this cleans out only the older and obsolete archives.
Keeping the most recent
Example would be it'll clear out older firefox archived packages, but keep the currently installed archive package.
(edit: though if server Firefox would be irrelevant.....)

---

### Post by kustomjs on 2017-10-12
whats the best way on removing old kernels?

---

### Post by darkod on 2017-10-12
1. Use uname -r to check loaded kernel. DO NOT remove that one.
2. Use dpkg --list | grep linux-image to list all kernels. The ones with ii in front are currently installed.
3. To remove use sudo dpkg --purge linux-image-XXXX-generic. Leave the two newest kernels and the one currently loaded.

---

### Post by kustomjs on 2017-10-12
this is what images I have loaded:

```
tim@mail:~$ dpkg --list | grep linux-image
pi  linux-image-4.4.0-62-generic       4.4.0-62.83                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-75-generic       4.4.0-75.96                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-77-generic       4.4.0-77.98                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic       4.4.0-78.99                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-79-generic       4.4.0-79.100                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-81-generic       4.4.0-81.104                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic       4.4.0-83.106                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-87-generic       4.4.0-87.110                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-89-generic       4.4.0-89.112                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-91-generic       4.4.0-91.114                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-92-generic       4.4.0-92.115                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic 4.4.0-62.83                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-75-generic 4.4.0-75.96                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-77-generic 4.4.0-77.98                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic 4.4.0-78.99                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-79-generic 4.4.0-79.100                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-81-generic 4.4.0-81.104                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-83-generic 4.4.0-83.106                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-87-generic 4.4.0-87.110                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-89-generic 4.4.0-89.112                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-91-generic 4.4.0-91.114                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-92-generic 4.4.0-92.115                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-93-generic 4.4.0-93.116                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                4.4.0.93.98                                amd64        Generic Linux kernel image 
```

when I try to remove one of them I get this error:

xx@mail:~$ sudo dpkg --purge linux-image-4.4.0-89-generic
[sudo] password for xx:
dpkg: dependency problems prevent removal of linux-image-4.4.0-89-generic:
 linux-image-extra-4.4.0-89-generic depends on linux-image-4.4.0-89-generic.

dpkg: error processing package linux-image-4.4.0-89-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-89-generic
xx@mail:~$

---

### Post by darkod on 2017-10-13
But that one says 'pi' in the first column, not 'ii'. Try ones with 'ii'.

Also dependencies can be broken if apt-get ran out of space. In that case the alternative is removing kernel files manually with rm from /boot. Be careful though, and as said never remove the current running kernel or the two newest ones. The initrd and the linux files are the biggest ones in /boot. You can ignore the rest for now... Just remove the biggest ones for each -XX- kernel versio nthat you want to remove. Once you have about 200MB free in /boot, apt-get will start working and you can continue cleaning up with apt-get.

Don't forget, this is only related to /boot. You also have to clean space on root partition, delete some of the data there.

---

### Post by kustomjs on 2017-10-13
Alright when I did that it crash the VPS server and right now I am in recovery and I am still lost how a 500gb mail server can use all of that 500gb that quick I only got 15 customers on this mail server with only 100meg mail boxes and I am using iredmail with mysql.

---

### Post by darkod on 2017-10-13
Recovery? If you entered with 'drop to root shell' you need to remount / as RW, you know that?

Plus, I didn't really understand which part crashed the server, deleting kernels with rm?

Post the content of your /boot:
```
df -h
uname -r
ls /boot/
```

Then we can help with more detailed commands if you need it...

---

### Post by kustomjs on 2017-10-13
here is a image since I had to do kvm console due to system crash
.[ATTACH=CONFIG]277095[/ATTACH]

Yes I crashed the system after removing the older kernels and I left the 2 newest ones in there.

---

### Post by LHammonds on 2017-10-13
```

ii  linux-image-4.4.0-87-generic
pi  linux-image-4.4.0-89-generic
iF  linux-image-4.4.0-91-generic
iF  linux-image-4.4.0-92-generic

```

This right here would have freaked me out looking at it.

"ii" means it is installed...making me think the last good kernel installed is 4.4.0-87

"pi" means it wants to be purged but is currently installed so 4.4.0-89 is subject to being removed with an "apt-get autoremove" command.

"iF" means these are installed but failed during install and since these are the 2 newest kernels, I would suspect you were out of room when 4.4.0-91 tried to install and 4.4.0-92 failed as well.

I would use 4.4.0-87 as the current kernel to boot and purge all others.

You will need to clean up the root partition too since it was unfortunate that everything else is in the same partition (thus if /var or /opt fill up, it affects the entire OS....you should NEVER let root fill up)

Once room has been made on /boot and the other partition (and only then), you can then do an "apt-get upgrade" to install the latest kernel...although you will likely need to do "apt-get install -f" to fix the packages that could not finish installing.

Also, the "uname -a" command gives you the kernel that is loaded which you can match to the files in /boot.

To fix where you are at right now may require help from others more experienced in this kind of situation.  A Live CD may help you with clearing out files so you can repair the boot partition.

I avoid these situations by manually setting up the partition during the initial install of the OS.  See my sig for a link to a tutorial on installing Ubuntu Server...it has a detailed section that talks about how to carve up the partitions to prevent this and help manage growth no matter where it is at on the server.

Speaking of growth, you said you didn't know what was taking up space.  The small /boot partition is obvious, old kernels were never purged and just kept consuming space.  That happens on every system.  Solution is to purge old kernels at least every couple months depending on our large your /boot partition was initially configured.  As for the rest of the space, you can find out what is taking up the most space by using the following command in the various directories:

```
du -sh /usr /opt /home /tmp /var /srv
```

Example output:
```

880M    /usr
4.0K    /opt
44K     /home
32K     /tmp
950M    /var
4.0K    /srv

```

Let's say you didn't expect /var to be that big, you then run this command:

```
du -sh /var/*
```

Example output:
```

8.4M    /var/backups
415M    /var/cache
4.0K    /var/crash
357M    /var/lib
4.0K    /var/local
0       /var/lock
22M     /var/log
4.0K    /var/mail
4.0K    /var/opt
0       /var/run
16K     /var/scripts
32K     /var/spool
12K     /var/tmp
150M    /var/www

```
We now see that the largest directory under /var is cache @ 415 MB, then lib @ 357 MB and www @ 150 MB

I hope this helps prevents future mishaps.

LHammonds

---

### Post by darkod on 2017-10-13
Hold on, if you are using systemrescuecd to boot, that changes things a lot. The commands you issue give results from the live rescuecd session, not from your installation.

You need to chroot into your installation so that you work from inside it... And also don't forget to mount your /boot partition which I don't see on that rescuecd screenshot.

So first list all disks to make sure which is your partition. One command you should be able to use is:
```
lsblk
```

That should list all disks and partitions. After we know that we can plan the chroot.

---

### Post by kustomjs on 2017-10-13
I dont know really how to mount the system in vps but here is the command you wanted:

[ATTACH=CONFIG]277104[/ATTACH]

but in main system as /dev/mapper/mail--vg-root its still showing full disk.

---

### Post by darkod on 2017-10-13
OK. So, /dev/vda1 is your /boot. And you also have LVM on the server, that you need to activate (although I think rescuecd does that for you).

To make sure the LVM is activated, and unmount any default mount point, try the following:
```
vgchange -ay
umount /dev/mail-vg/root   (I believe that is your LV name, if not adjust it accordingly)
```

After that is done, you are ready to temporarily mount everything and chroot:
```
mount /dev/mail-vg/root /mnt
mount /dev/vda1 /mnt/boot
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt
```

After that you should be inside your OS chroot. Stop at this point and show the output of:
```
ls /boot
```

Do not do anything else, leave the terminal session open...

---

