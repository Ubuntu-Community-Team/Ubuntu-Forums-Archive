---
title: "fsck a RAID1 drive?"
date: 2009-09-06
forum: Server Platforms
---

### Post by rocknrollmouse on 2009-09-06
I have ubuntu server running on mirrored drives.  

If I check the free space with df -h I'm told theres 33G used out of 48G; however fdisk -l and mdadm --detail for the same drive, I'm told its 398G (no used space info).

Suspecting something was wrong I ran fsck -n, which reported inode errors.

How do I run fsck on my mirrored drive - as its root(/) and includes boot I can't umount it; but, as it mirrored, if I boot from I live disk I only see the real drives not md0?

Does anyone know of a problem with df or is there another way to check disk usage?

Many thanks.

---

### Post by gombadi on 2009-09-06
> 
How do I run fsck on my mirrored drive - as its root(/) and includes boot I can't umount it; but, as it mirrored, if I boot from I live disk I only see the real drives not md0?


All you have to do in the live cd is to build the array. Here are some instruction I wrote for myself in the past and they should still work -

If you know the partitions then
```

modprobe md
modprobe raid1
mdadm /dev/md? --run /dev/sd?? /dev/sd??
mount /dev/md0 /mnt/md0

```

or if you don't know the partitions then
```

mdadm --examine --scan /dev/hd?? >> /etc/mdadm/mdadm.conf
vim /etc/mdadm/mdadm.conf # edit file to remove rubbish
mdadm --assemble --scan

```

Update the above for your situation.

Also big warning - messing around with this type of thing can destroy your data - Make sure you have backups.

---

### Post by rocknrollmouse on 2009-09-06
hi gombadi,

thanks for the instructions, but can you give me a tip as to which live disk to use?

[INDENT](I downloaded the desktop version that matched my server - 6.10
unfortunately it doesn't recognise mdadm - I get "command not found")[/INDENT]

regards,
simon

---

### Post by rocknrollmouse on 2009-09-07
OK, booted from 6.10 desktop and changed /etc/apt/sources.list to point at the old repros:

```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu edgy-security universe
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security universe

```

then loaded mdadm via:
```
sudo apt-get update
sudo apt-get install mdadm
```

running gombadi's instructions, I get to the first mdadm line, which gives an unexpected response:
```
$ sudo modprobe md
$ sudo modprobe raid1
$ sudo mdadm /dev/md0 --run /dev/hda1 /dev/hdc1

mdadm: /dev/hda1 does not appear to be an md device
mdadm: /dev/hdc1 does not appear to be an md device
```

can anyone spot where I'm going wrong?

---

### Post by gombadi on 2009-09-07
> 
OK, booted from 6.10 desktop and changed /etc/apt/sources.list to point at the old repros


Oh 6.10 - Yes that is getting a bit old and unsupported. Something for your to do list - upgrade to a newer version ;-)

Can you boot your system normally and then post the output of the following -
```

df -h
cat /proc/mdstat

```

It will help us track down what is going on.

---

### Post by rocknrollmouse on 2009-09-07
yes, I was hoping to get that to the top of the "to do list", but I think I'll better get the filesystem stable first (some excellent how tos for getting to LTS versions I've lined up!)

Here are the outputs you asked for:

df -h
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               48G   30G   16G  66% /
varrun                502M  144K  502M   1% /var/run
varlock               502M  4.0K  502M   1% /var/lock
procbususb             10M  108K  9.9M   2% /proc/bus/usb
udev                   10M  108K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm


cat /proc/mdstat
> Personalities : [raid1]
md1 : active raid1 hdc2[0] hda2[1]
      2032128 blocks [2/2] [UU]

md0 : active raid1 hdc1[0] hda1[1]
      388676480 blocks [2/2] [UU]

unused devices: <none>


---

### Post by koenn on 2009-09-07
It's probably easier to force the system to do an fsck at reboot. It will mount  /  readonly so it can safely be checked and repaired.

there used to be an option to shutdown to do this but apparently it got removed. You can emulate it by

```

sudo touch /forcefsck
sudo shutdown -r now

```

DISCLAIMER : I assume this also works on software raid like yours, but I've never tried it.

---

### Post by rocknrollmouse on 2009-09-18
Hi Koenn,

The forcefsck appeared to work, not sure if the touch part of the command was ment to create a log file, but I couldn't find one.

All that done, but the drives still showing as only 48Gb (using fd -h).  

As this is not looking like an fsck problem, but a drive issue, should I create a new post with an appropriate heading?

---

### Post by koenn on 2009-09-18
the touch command puts a file in /.
The presence of that file during boot tells the system to do fsck on / before it's mounted read-write 

Your issue seems to be discrepancies in disk usage / free space, so maybe it's best to make a new thread along those lines.
piece pf advise : post (in code tags) the actual commands + their output  that make you think there is a problem.

---

