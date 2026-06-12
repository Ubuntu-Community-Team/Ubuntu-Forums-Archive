---
title: "Server: Can't see why my / partition is full"
date: 2009-08-13
forum: Server Platforms
---

### Post by ubitos on 2009-08-13
Hi everyone,

Back from summer break I get a look at my ubuntu server and see:

```
/$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             464M  464M     0 100% /
varrun                7.9G  196K  7.9G   1% /var/run
varlock               7.9G     0  7.9G   0% /var/lock
udev                  7.9G   96K  7.9G   1% /dev
devshm                7.9G     0  7.9G   0% /dev/shm
/dev/sda1             950M   36M  867M   4% /boot
/dev/sda8             422G  1.5G  399G   1% /data
/dev/sda7             924G  177G  702G  21% /home
/dev/sda10            8.8G  149M  8.2G   2% /tmp
/dev/sda5              19G  1.7G   16G  10% /usr
/dev/sda6             9.3G  617M  8.2G   7% /var
/dev/sdb1             1.4T  319G  999G  25% /media/external_drive1
```

And I didn't like to see that my / partition was full. So, to see what could be freed, I did:

```
$ sudo du -s /* | sort -nr
du: cannot access `/proc/8812/task/8812/fd/4': No such file or directory
du: cannot access `/proc/8812/task/8812/fdinfo/4': No such file or directory
du: cannot access `/proc/8812/fd/4': No such file or directory
du: cannot access `/proc/8812/fdinfo/4': No such file or directory
333268230       /media
184489136       /home
1589836 /usr
1327040 /data
479064  /var
104848  /lib
18564   /boot
7990    /etc
6698    /sbin
4657    /bin
2409    /lib32
101     /dev
36      /tmp
12      /lost+found
6       /root
1       /srv
1       /opt
1       /mnt
1       /initrd
0       /vmlinuz
0       /sys
0       /proc
0       /lib64
0       /initrd.img
0       /cdrom

```

And I'm very surprised to see that the only "big" stuff in / is /lib which accounts for 104M, the rest is very small: all other big dirs are on different partitions. How can I know what occupies the remaining 350M of / ???? :confused:

Any help would be very much appreciated,
Thanks in advance.

---

### Post by jbcola on 2009-08-13
Maybe there is a logfile written somewhere, you could try to use the "lsof" command to find the growing file...

---

### Post by Wim Sturkenboom on 2009-08-13
There might be deleted files that are still 'in use' by an application. *du* will not show that but *df* does. *lsof* can help and a server reboot should definitely clear it.

---

### Post by ubitos on 2009-08-13
Thanks for your replies!
But rebooting didn't clean my / space. I'll search with lsof...

---

### Post by ubitos on 2009-08-13
Thank you, but I can't see any big file in the output of lsof. Rebooting puts me back to 100% usage of / and I can't easily follow what's growing if it's full from the beginning. Any idea?

---

### Post by phillw on 2009-08-13
try it with du -a ...   (I'd suggest sending the output to a file in your home directory)

Hope that helps

Phill.

---

### Post by lykwydchykyn on 2009-08-13
> **phillw said:**
> try it with du -a ...   (I'd suggest sending the output to a file in your home directory)

Hope that helps

Phill.

I'd also add the -x switch, so that it only reads from / and not from the other mounted filesystems; e.g.:
 du -ax / |sort -nr >~/filesizes.txt

---

### Post by ubitos on 2009-08-13
> **lykwydchykyn said:**
> I'd also add the -x switch, so that it only reads from / and not from the other mounted filesystems; e.g.:
 du -ax / |sort -nr >~/filesizes.txt

Thanks, I'm learning so at least that's good.

Top of the produced file is:
```
126657  /
104848  /lib
91248   /lib/modules
91247   /lib/modules/2.6.24-16-server
76287   /lib/modules/2.6.24-16-server/kernel
55913   /lib/modules/2.6.24-16-server/kernel/drivers
13238   /lib/modules/2.6.24-16-server/ubuntu
11538   /lib/modules/2.6.24-16-server/kernel/drivers/net
9594    /lib/modules/2.6.24-16-server/kernel/net
8650    /lib/modules/2.6.24-16-server/kernel/fs
7992    /etc
7981    /lib/modules/2.6.24-16-server/kernel/drivers/media
6865    /lib/modules/2.6.24-16-server/ubuntu/sound
6864    /lib/modules/2.6.24-16-server/ubuntu/sound/alsa-driver
6698    /sbin
```
And (so far) I don't see any descrepancy in it. I'm still looking, but I noticed something weird after reboot:

```
$ sudo df -ah
Filesystem            Size  Used Avail Use% Mounted on
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                7.9G  176K  7.9G   1% /var/run
varlock               7.9G     0  7.9G   0% /var/lock
udev                  7.9G   96K  7.9G   1% /dev
devshm                7.9G     0  7.9G   0% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda1             950M   36M  867M   4% /boot
/dev/sda8             422G  1.5G  399G   1% /data
/dev/sda7             924G  177G  702G  21% /home
/dev/sda10            8.8G  149M  8.2G   2% /tmp
/dev/sda5              19G  1.7G   16G  10% /usr
/dev/sda6             9.3G  617M  8.2G   7% /var
securityfs               0     0     0   -  /sys/kernel/security
/dev/sdb1             1.4T  319G  999G  25% /media/external_drive1
```

There is no output for / anymore !??
I still see:
```
$ sudo df -ha /
Filesystem            Size  Used Avail Use% Mounted on
-                     464M  464M     0 100% /
```

I can go into / and list /lib and /etc, so I guess it is mounted. However I don't see my sda9 partition anymore when doing:
```
$ sudo mount
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/sda8 on /data type ext3 (rw,relatime,usrquota)
/dev/sda7 on /home type ext3 (rw,relatime,usrquota,grpquota)
/dev/sda10 on /tmp type ext3 (rw,relatime)
/dev/sda5 on /usr type ext3 (rw,relatime)
/dev/sda6 on /var type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/external_drive1 type ext3 (rw)
```

I guess that's part of the problem.
My /etc/fstab is:
```
$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=0eedb552-20db-474e-ba4b-7ab499d95406 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=e8fc913e-e0f8-4f47-81c2-c2c50a19eedd /boot           ext3    relatime        0       2
# /dev/sda8
UUID=5f208520-e64b-41ae-aaee-ad8de0d7dda2 /data           ext3    relatime,usrquota        0       2
# /dev/sda7
UUID=75c88bf1-beeb-4827-a8de-e4a7f64e28ef /home           ext3    relatime,usrquota,grpquota        0       2
# /dev/sda10
UUID=5b0a38cc-c01f-40f6-a370-704225c8f323 /tmp            ext3    relatime        0       2
# /dev/sda5
UUID=2b116685-90e7-4bb4-8e52-6c2c0d35a3e0 /usr            ext3    relatime        0       2
# /dev/sda6
UUID=e5105e12-54c7-4cb3-bbe7-f0012ae9ad1e /var            ext3    relatime        0       2
# /dev/sda2
UUID=c765b865-3b52-4f5f-b4aa-565678c817fa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1      /media/external_drive1  ext3    defaults        0       2
```

Anything related to the "errors=remount-ro" flag?
Thanks again!

---

### Post by phillw on 2009-08-13
As the / is full - it's reporting an error. so, it's being mounted read-only.

Very odd that you're not seeing where the room is with du . I'm afraid the answer to that one is beyond my expertise.

Sorry I couldn't be of more help.

Phill.:(

---

### Post by lykwydchykyn on 2009-08-13
I would recommend at this point booting to a liveCD so you can take a look at the partition in isolation.  Maybe one of your mountpoints is not empty?

the errors=remount-ro is a pretty standard flag for the root filesystem, it means if there are errors on the filesystem it will be remounted read-only (to avoid compounding the errors).  I don't know if a partition being full would trigger that kind of error, usually it results in X not starting and a message during bootup to run fsck or something.

---

### Post by ubitos on 2009-08-13
> **phillw said:**
> As the / is full - it's reporting an error. so, it's being mounted read-only.

Very odd that you're not seeing where the room is with du . I'm afraid the answer to that one is beyond my expertise.

Sorry I couldn't be of more help.

Phill.:(

I'm not seeing it SO FAR, which means I may not have looked hard enough... Anyway, thanks again.

---

### Post by ubitos on 2009-08-14
> **lykwydchykyn said:**
> I would recommend at this point booting to a liveCD so you can take a look at the partition in isolation.  Maybe one of your mountpoints is not empty?

I'm still searching... Can you guide me here please: how do I know if a mount point is empty: if I du it before mounting and it returns some non-negligeable size?

> **lykwydchykyn said:**
> the errors=remount-ro is a pretty standard flag for the root filesystem, it means if there are errors on the filesystem it will be remounted read-only (to avoid compounding the errors).  I don't know if a partition being full would trigger that kind of error, usually it results in X not starting and a message during bootup to run fsck or something.

Is the error responsible for the read-only remounting written somewhere? This could help me see if there is another problem than room space.

Again, and again: many thanks!

---

### Post by ubitos on 2009-08-14
As suggested by my rescuers here, I saw recommendations to use lsof on [here]("http://www.linuxjournal.com/node/1000432")
but doesn't seem to help me much (which makes sense considering that rebooting doesn't clear space):

```
$ sudo lsof | grep deleted
init         1     root    0u      CHR                5,1                 536 /dev/console (deleted)
init         1     root    1u      CHR                5,1                 536 /dev/console (deleted)
init         1     root    2u      CHR                5,1                 536 /dev/console (deleted)
mysqld    5207    mysql    4u      REG               8,10        0      24577 /tmp/ibPchSG3 (deleted)
mysqld    5207    mysql    5u      REG               8,10       87      24578 /tmp/ibkwpEga (deleted)
mysqld    5207    mysql    6u      REG               8,10        0      24579 /tmp/ibtYKqQg (deleted)
mysqld    5207    mysql    7u      REG               8,10        0      24580 /tmp/ib9pZMqn (deleted)
mysqld    5207    mysql   11u      REG               8,10        0      24581 /tmp/ibsWSwdu (deleted)

```

I'd prefer avoid the liveCD boot (server is in remote location, where other machines are running and relevant administrators currently on vacation...). But I'll do in a few days if necessary.
#-o

---

### Post by lykwydchykyn on 2009-08-14
> **ubitos said:**
> I'm still searching... Can you guide me here please: how do I know if a mount point is empty: if I du it before mounting and it returns some non-negligeable size?

Yeah, basically.  The idea is maybe something got chucked inside one of your mountpoints before the disk got mounted.  The space would be used on /, but you wouldn't be able to see it because another filesystem is mounted there.

Just a theory; if it were the case I'd be kind of surprised because I believe mount requires some kind of a flag to mount a non-empty mountpoint.  You'd at least expect errors in the log.

> 
Is the error responsible for the read-only remounting written somewhere? This could help me see if there is another problem than room space.

Again, and again: many thanks!

No, "errors=ro" does not indicate that there IS an error, it's a fstab flag that tells mount what to do if WHEN an error happens.  It's just a setting, in other words.

---

### Post by PatrickVogeli on 2009-08-14
sudo apt-get clean may do the trick. Could you look how much space is filled under /var/cache/apt/archives?

---

### Post by lykwydchykyn on 2009-08-14
> **PatrickVogeli said:**
> sudo apt-get clean may do the trick. Could you look how much space is filled under /var/cache/apt/archives?

/var is on a totally different filesystem here.

---

### Post by phillw on 2009-08-14
[SIZE=2]::SIGH::

I can't believe you're still having problems[/SIZE]

[SIZE=2]This kind soul explains quite a lot - I had a good read & thought it may assist you.

[http://tinyurl.com/bftl8e](http://tinyurl.com/bftl8e)[/SIZE]

The entire thread is here                        [http://www.debian-administration.org/article/What_to_do_when_the_root_partition_is_full](http://www.debian-administration.org/article/What_to_do_when_the_root_partition_is_full)

[SIZE=2]
Some more thoughts on the matter can be found here...

[https://bugs.launchpad.net/ubuntu/+bug/217389](https://bugs.launchpad.net/ubuntu/+bug/217389)


Regards,

Phill.[/SIZE]

---

### Post by ubitos on 2009-08-17
> **phillw said:**
> 

[SIZE=2]This kind soul explains quite a lot - I had a good read & thought it may assist you.

[http://tinyurl.com/bftl8e](http://tinyurl.com/bftl8e)[/SIZE]

The entire thread is here                        [http://www.debian-administration.org/article/What_to_do_when_the_root_partition_is_full](http://www.debian-administration.org/article/What_to_do_when_the_root_partition_is_full)

Thx, but all this assumes that du tells me what occupies space. I wish it di in my case!

> **phillw said:**
> [SIZE=2]
Some more thoughts on the matter can be found here...

[https://bugs.launchpad.net/ubuntu/+bug/217389](https://bugs.launchpad.net/ubuntu/+bug/217389)


Regards,

Phill.[/SIZE]

That sounds interesting, thank you! Post#7 (very recent) on this thread mentions an issue when backing-up on an external drive that is no longer mounted. I did have backup cron jobs, and (I forgot to mention, sorry ):???: ), my USB drive was unmounted when I was back. It seems that this could have atempted to backup to / instead, which in my case would be a disaster. I'll search in this direction and let you all know.
Best.

---

### Post by ubitos on 2009-08-17
GREAT GREAT GREAT!!! Solved! :P

That was it: as my /dev/sdb1 was no longer mounted on /media/external/external_drive1, my latest backups did write on /media/external_drive1/ but on the / partition.
The trick is that, as I remounted my external drive, du no longer accessed the / space used by the misplaced backup files, as /media/external_drive1/ correctly directed it to the external disk. But df knew.

Solution is simple:
```
sudo umount /media/external_drive1
ls /media/external_drive1/ #surprise: not empty!!!
sudo rm /media/external_drive1/*
```
and reboot.

Thank you so much to all of you for your help, especially phillw for flagging the other thread!
Bye.

---

### Post by ubitos on 2009-08-17
I forgot: of course, I'm now adding something like:

```
volume="/media/external_drive1"

if mount|grep $volume; then
#tar what I need
fi
```

in my backup scripts to avoid this.
Cheers.

---

