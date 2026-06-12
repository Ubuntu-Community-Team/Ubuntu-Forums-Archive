---
title: "strange virtual disk size - please help"
date: 2015-10-24
forum: Virtualisation
---

### Post by misha6 on 2015-10-24
Hi, I really need help with the following. 

I am using a Mac Book Pro on which I am running Ubuntu with VirtualBox. 
I set the virtual disk size to 40Gb dynamically allocated. After a couple of weeks the virtual disk size limit of 40Gb is reached. 
My / folder contains only 8,4 Gb of Data. So whats taking all that space??? 

Thanks for your help.
Misha

---

### Post by TheFu on 2015-10-24
Please post this output:
```
$ df -h
```
and
```
$ du -sh /*
```

Use [code tags]("http://blog.jdpfu.com/code_tags") when you post so things are easy to read. I'm too old to parse things that are hard to read.

---

### Post by misha6 on 2015-10-24
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       37G  7,6G   27G  22% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            2,0G  4,0K  2,0G   1% /dev
tmpfs           396M  956K  395M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,0G  152K  2,0G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sr0       56M   56M     0 100% /media/misha/VBOXADDITIONS_4.3.30_1016101




```

```

9,7M /bin
154M /boot
4,0K /cdrom
4,0K /dev
13M /etc
1,7G /home
0 /initrd.img
0 /initrd.img.old
1,1G /lib
4,0K /lib64
16K /lost+found
56M /media
4,0K /mnt
16M /opt
du: cannot access &#8216;/proc/2313/task/2313/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/2313/task/2313/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/2313/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/2313/fdinfo/4&#8217;: No such file or directory
0 /proc
12K /root
du: cannot access &#8216;/run/user/1000/gvfs&#8217;: Permission denied
1,2M /run
12M /sbin
4,0K /srv
0 /sys
16K /tmp
4,1G /usr
534M /var
0 /vmlinuz
0 /vmlinuz.old/

```

---

### Post by TheFu on 2015-10-24
7,6G  is used by the OS currently.
I think vHDDs only grow, so if you've had large media copied into the VM, it would have to grow to hold it, then it won't reduce. Also, there is the swap partition, but that  doesn't grow after creation. **free  -m** will show the current size and usage.

My main desktop uses 13G and that is after running it on 10.04 and doing 2 upgrades. I'm cautious NOT to have media stored on that VM.

Last, are you using snapshots a bunch or doing something else strange outside the VM with this virtual storage?

You can use vboxmanage to move the storage into another vHDD file. I don't remember the options or specific command. The manpage will have that.

---

### Post by afz12 on 2015-10-24
Hi misha6

I found the same virtual size creepage with Virtual box but bleachbit seemed to resolve this at

[http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

If you have a windows VM then ccleaner from Piriform has a "wipe free space" option - bleachbit seems to be a Linux copy cat version. 

[https://www.piriform.com/ccleaner](https://www.piriform.com/ccleaner)

However bleachbit can be a bit brutal and your VM may complain that the disk is full (with zeros I guess) during its execution. If so it might pay to stop it and reboot the VM. However some of my windows VM had bloated out to 30 GB or more, now they are at 6 ~ 8 GB reported size and much quicker to transfer to external USB drives .

---

