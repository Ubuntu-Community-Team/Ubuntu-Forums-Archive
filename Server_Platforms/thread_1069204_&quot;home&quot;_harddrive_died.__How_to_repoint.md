---
title: "&quot;/home&quot; harddrive died.  How to repoint?"
date: 2009-02-13
forum: Server Platforms
---

### Post by fizgig on 2009-02-13
When I installed ubuntu server, I used /dev/sd**c**1 for the root partition and /dev/sd**d**1 for my home folder as shown in the section of my /etc/fstab below.

```
# /dev/sdc1
UUID=8ee09432-be05-4f30-b20a-0c231acfe335 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd1
UUID=002e5902-eb84-4adf-af68-1bdf74eb5af9 /home           ext3    relatime        0       2
```Trouble is that my drive /dev/sdd died.

I don't have much on my root partition and don't plan to store much more in my home folder (I use other hard drives for main storage) so I just want to make /home also be on the same harddrive as the root.

Do I just change

```
UUID=002e5902-eb84-4adf-af68-1bdf74eb5af9 /home           ext3    relatime        0       2
```to match the UUID of the good drive and add a path like this?
```

UUID=8ee09432-be05-4f30-b20a-0c231acfe335**/home**    /home               ext3    relatime,errors=remount-ro 0       1
```Also, things are acting a little funny.  When I type **fdisk -l**, I thought I usually get back a list of hard disks and info about them (can't recall for sure though) but I get nothing back.  In addition, when I want to learn about /dev/sdc, I try to type **fdisk -l /dev/sdc** but I get nothing there as well.  Finally, I did **df -h** hoping to see how much of /dev/sdc is there but it doesn't seem to be listed - just my storage drives at the bottom and some other stuff I don't understand above:

```
Filesystem            Size  Used Avail Use% Mounted on
varrun                379M  204K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   76K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
/dev/mapper/vg2-backup
                      458G  418G   17G  97% /media/500gb-backup
/dev/mapper/vg1-storage
                      458G  418G   17G  97% /media/500gb
```How come I don't see filesystem "/" and how much space there is left on it?  How do I repoint /home to the good hard drive?

Me very confused.

---

### Post by conjur3r on 2009-02-13
Comment out the /home (sdd1) part in /etc/fstab and your system will begin to store its home stuff in sdc1 by default as it is the root partition.  All mount points that aren't explicitly defined will use the root partition.

Did you try putting sudo in front of fdisk?

---

### Post by fizgig on 2009-02-13
Thanks for the tip.  I commented out the home line and the server still lives.

Trouble is, **fdisk -l **or **df -h** still doesn't show the space used/left on the root partition.  I still get the same:

```
root@massive:/home# df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                379M  180K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   80K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
/dev/mapper/vg1-storage
                      458G  418G   17G  97% /media/500gb
/dev/mapper/vg2-backup
                      458G  418G   17G  97% /media/500gb-backup
```

And I'm running both commands as root.

Any idea why I don't have an entry for root?  It has to be mounted since the system boots and I can ssh into it right?

---

### Post by conjur3r on 2009-02-13
Does the root partition come up when you run **mount**?  If it still doesn't work, try temporarily mounting /dev/sdc1 to /mnt to invoke any error messages it may have.  Check your logs to see if anything relates too.

---

### Post by fizgig on 2009-02-13
Here are the results of the mount command run as root:

```
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/mapper/vg1-storage on /media/500gb type ext3 (rw,noexec,nosuid,nodev)
/dev/mapper/vg2-backup on /media/500gb-backup type ext3 (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
```


Don't see anything too special in the error logs.

Why can't I see what is mounted as the root directory?  Why wont **fdisk -l** show me anything?

---

