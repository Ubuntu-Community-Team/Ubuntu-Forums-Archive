---
title: "Can't update. Disk full?"
date: 2011-06-18
forum: Server Platforms
---

### Post by odbo on 2011-06-18
Sorry for the newbie question, but "apt-get update" is giving me a full disk error. And "df -h" shows that /dev/mapper/ubuntu-root is using 100% of disk space. Any tips is much appreciated!

I'm running a 10.10 server and I'm pretty new to linux.

---

### Post by crispy_420 on 2011-06-18
How big is your drive? Is buying a bigger drive and imaging over to it an option for you?

Either that or remove data through moving it off or deleting.

---

### Post by odbo on 2011-06-18
I've got three 250Gb drives and a 2Tb usb-drive for backup. None of them are full really. But the "ubuntu-root"-file (?) seems to grow bigger and bigger. I guess the "ubuntu-root" is not really a physical hard-drive, but it seems to clog up the system somehow...

---

### Post by odbo on 2011-06-18
This link was pretty helpful: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Tried this:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Worked fine! But the "/dev/mapper/ubuntu-root" is still 100%.

---

### Post by BkkBonanza on 2011-06-18
Can you post the output of the command,  

df -h

This will help us know how your partitions are mounted, size and utilization.
It sounds like you made a small root partition when you installed and now that is limiting you. 

Another useful command to see where space is used:

sudo du --max-depth=1 -xh /

---

### Post by ian dobson on 2011-06-18
Hi,

Maybe cleanout /var/log and a sudo apt-get purge might also help.

Regards
Ian Dobson

---

### Post by odbo on 2011-06-18
> **BkkBonanza said:**
> Can you post the output of the command,  

df -h

This will help us know how your partitions are mounted, size and utilization.
It sounds like you made a small root partition when you installed and now that is limiting you. 

Another useful command to see where space is used:

sudo du --max-depth=1 -xh /

Here's the output of df -h
```
Filsystem            Size  Used Avail Use% Montert pÃ¥
/dev/mapper/ubuntu-root
                      220G  220G     0 100% /
none                  2,0G  284K  2,0G   1% /dev
none                  2,0G     0  2,0G   0% /dev/shm
none                  2,0G  372K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
/dev/sda1             228M  116M  101M  54% /boot
/dev/sdb1             233G  196G   38G  85% /media/berlin
/dev/sdc1             233G   16G  218G   7% /media/paris
```And the "sudo du --max-depth=1 -xh /"
```
2,0K    /boot
16K    /root
0    /sys
20M    /opt
5,8M    /etc
0    /proc
16K    /lost+found
6,6M    /home
4,0K    /mnt
0    /dev
6,6M    /sbin
4,0K    /selinux
217G    /media
12K    /srv
315M    /var
798M    /lib
880M    /usr
232K    /tmp
7,7M    /bin
219G    /

```

---

### Post by BkkBonanza on 2011-06-18
Looks like you have 217G in /media, and 218G free in /media/paris
I'd suggest moving whatever you can from /media to /media/paris

Or if you don't want files there then you might consider reducing your sdc1 partition and making another partition that you can mount under /media and move the files there.

The main thing is to free up space under /media because that is the bulk of all your space on ub ubuntu-root.

You can change a partition size of sdc1 with Gparted (System, Administration, GParted if it's installed or else use Synaptics to install). But just moving the files will be easier and safer.

---

### Post by SACHINVD on 2011-06-18
You can remove unnecessary packages using command
```
sudo apt-get autoremove
``` 

or you can manually delete packages from location

/var/cache/apt/archives/

---

### Post by odbo on 2011-06-18
Thanks everybody for helping out! I've checked the cache and log directories and they're not that big.

Maybe the external usb-drive is causing the problems? I've mounted it as usb0 in /media. There's actually no files in /media that accounts for the 217G size. I'll keep on digging...:)

---

