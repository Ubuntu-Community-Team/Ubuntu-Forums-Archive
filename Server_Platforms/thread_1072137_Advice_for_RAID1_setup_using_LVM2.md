---
title: "Advice for RAID1 setup using LVM2?"
date: 2009-02-17
forum: Server Platforms
---

### Post by yther on 2009-02-17
Hi!

I've got a shiny new system here and I am preparing to set up a RAID1 on it.  Main OS is already installed and here is what I have now:

```
rassilon@miharu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              94G  3.2G   86G   4% /
tmpfs                 4.0G     0  4.0G   0% /lib/init/rw
varrun                4.0G  252K  4.0G   1% /var/run
varlock               4.0G     0  4.0G   0% /var/lock
udev                  4.0G  2.9M  3.9G   1% /dev
tmpfs                 4.0G     0  4.0G   0% /dev/shm
lrm                   4.0G  2.4M  3.9G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             9.4G   26M  8.9G   1% /boot
/dev/sda9             289G  124G  150G  46% /home
/dev/sda8              94G  700M   89G   1% /tmp
/dev/sda7              94G  1.3G   88G   2% /var

```

As you can see, all of that is on a single physical drive.  I also have two 1TB drives which will be configured as RAID1.  When I went to set that up tonight, the tool told me mirroring was not allowed unless I had space available on *three* physical volumes.

I assume that, in addition to the two volumes that will be mirrored, I need some amount of space for the mirroring log or whatever it's called.  Am I close to the truth there?  :)

If that's so, how much space would I need to maintain a mirror for this?  My idea is, since I obviously gave far too much space to /var and /tmp, that I should remove the actual /tmp and symlink it to /var/tmp, thus freeing up all or part of what is now /dev/sda8 for the mirroring data.

I'm sure this is basic stuff here, but for some reason G was not my F tonight and I really couldn't find anything helpful.  Everyone seems to be using either hardware RAID or RAID5, and they just mention RAID1 in passing, which doesn't really help me.  So, any advice is appreciated!

---

### Post by bapoumba on 2009-02-17
Moved to Servers.

---

### Post by fjgaude on 2009-02-17
See if this link is useful:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Let us know how you are doing.

---

### Post by songshu on 2009-02-17
as you say the machine is still shining and you are reconsidering your partitioning an option would be to reinstall and use the installer to set up the raid during install, choose "partitioning" with the "alternate" install cd.

but if you want to install the raid on a running system thats possible as well and i actually recommend it, not because its easier but because it will also teach you whats going on in case one of the disks actually do break.

this is a good read for the raid
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

and from the same guy for resizing the partitions.
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

p.s.

i'm running several servers and money is not an object, but i always choose to use the Linux software raid, why? simple question: what do you do when the expensive raid controller dies? 
And especially with raid1 the linux raid performs very well and i prefer raid1 or raid10 over raid5 anytime because of performance.

---

### Post by netztier on 2009-02-17
> **yther said:**
> 
As you can see, all of that is on a single physical drive.  I also have two 1TB drives which will be configured as RAID1.  When I went to set that up tonight, the tool told me mirroring was not allowed unless I had space available on *three* physical volumes.


Nah. RAID1 is mirroring, period - I have two RAID1 arrays running with ease - two disks each. Only if you want a (hot) spare disk with your mirror, you'll need a third one - was "the tool" (which one?) assuming that a hot spare disk is default?

...Or you inadvertedly tried to configure a RAID5 setup, where three drives is the minimum.

regards

Marc

---

### Post by yther on 2009-02-18
OK, I'm having a look at those documents mentioned above, although they all seem to assume I'm setting up a RAID I'll be booting from, which is definitely not the case.  (In fact, every single howto I found had this extra layer of complexity.  Is it strange to boot from a *non-RAID* drive these days?)

BTW, installing **mdadm** pulls in **citadel**, a "groupware server."  Why the heck do I need that just for RAID management?!  :shock:  *Edit: After digging through deps, I'm guessing it got installed because it is, alphabetically, the first package to provide **mail-transport-agent**.  Serves me right for not having postfix installed yet, I suppose... stupid deps!*

Anyway, what I've done so far:

[LIST]
[*]Changed partition type of /dev/sdb1 and /dev/sdc1 to **fd** (I had put **8e** before)
[*]**mdadm --zero-superblock** on both of those
[*]And finally...
[/LIST]
```
$ sudo mdadm --create /dev/md0 --level=1 --raid-disks=2 /dev/sdb1 /dev/sdc1
mdadm: array /dev/md0 started.
$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sdc1[1] sdb1[0]
      976759936 blocks [2/2] [UU]
      [>....................]  resync =  0.4% (4883584/976759936) finish=162.9min speed=99426K/sec

unused devices: <none>

```

So far so good!  The rest looks pretty easy—create filesystem, mount, add to mdadm.conf and fstab.

[B]Edit:  I guess "mdadm" was the tool I'd been overlooking up to now.  Once I had that, this was downright easy!  Thank you all for your help, and I believe I'm basically done now.  :D

It looks like the drives will take about 2½ hours to synchronize... I'm going to bed![/B]

---

