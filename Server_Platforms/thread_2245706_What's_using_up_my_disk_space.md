---
title: "What's using up my disk space?"
date: 2014-09-25
forum: Server Platforms
---

### Post by bgood on 2014-09-25
According to a df -h output 19G is being used but I can't see what's using up all that space, from what I can see there's only about 10G actually being used, can anybody suggest where I should be looking to find the missing 9ishG?


root@NAS:~# uname -a
Linux NAS 3.2.0-68-generic #102-Ubuntu SMP Tue Aug 12 22:02:15 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

root@NAS:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1        30G   19G   11G  65% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           383M  5.3M  378M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   72K  1.9G   1% /run/shm
/dev/md0        8.1T  5.5T  2.7T  68% /media/Raid
/dev/sdf1        29G   11G   17G  39% /media/DTMICRO


root@NAS:~# du -sh /* --exclude=/media
4.0K    /accept_redirects
8.8M    /bin
175M    /boot
16K     /build
4.0K    /cdrom
4.0K    /dev
61M     /etc
du: cannot access `/home/bg/.gvfs': Permission denied
1.5G    /home
0       /initrd.img
0       /initrd.img.old
1.1G    /lib
3.4M    /lib32
4.0K    /lib64
0       /libnss3.so
16K     /lost+found
8.0K    /mnt
199M    /opt
du: cannot access `/proc/2710/task/2736/fd/45': No such file or directory
du: cannot access `/proc/4333/task/4333/fd/4': No such file or directory
du: cannot access `/proc/4333/task/4333/fdinfo/4': No such file or directory
du: cannot access `/proc/4333/fd/4': No such file or directory
du: cannot access `/proc/4333/fdinfo/4': No such file or directory
0       /proc
21M     /root
5.4M    /run
11M     /sbin
4.0K    /selinux
4.0K    /send_redirects
200K    /srv
0       /sys
504K    /tmp
5.1G    /usr
2.1G    /var
0       /vmlinuz
0       /vmlinuz.old
4.0K    /webmin-setup.out

---

### Post by nerdtron on 2014-09-25
Don't add * at the end of the du -sh. It doesn't give the correct data. Just use du -sh for the total usage.
My home folder says 468MB in total but du -sch * command inside the folder yields only 28 MB.
```
[root@nerdtron home]# ls
kenneth
[root@nerdtron home]# du -sch *
468M    kenneth
468M    total
[root@nerdtron home]# cd kenneth/
[root@nerdtron kenneth]# du -sch *
24K    Desktop
4.0K    Documents
4.0K    Downloads
4.0K    ec2.key
188K    mongo-1.5.4.tgz
4.0K    Music
4.0K    Pictures
24K    proj
4.0K    Public
23M    rpms
4.0K    Templates
4.0K    Videos
23M    total
[root@nerdtron kenneth]# 


```
But the correct value is 468MB when you use du -sch without a *.
```
[root@nerdtron kenneth]# pwd 
/home/kenneth
[root@nerdtron kenneth]# du -sh
468M    .

```

Not sure why. But at least you should get the idea. Try your du command again.

---

### Post by bgood on 2014-09-25
Thanks for the reply, tried the command as you suggested and it comes back as 11G:


root@NAS:~# du -sh / --exclude=/media
du: cannot access `/proc/14911/task/14911/fd/4': No such file or directory
du: cannot access `/proc/14911/task/14911/fdinfo/4': No such file or directory
du: cannot access `/proc/14911/fd/4': No such file or directory
du: cannot access `/proc/14911/fdinfo/4': No such file or directory
du: cannot access `/home/bg/.gvfs': Permission denied
11G     /

---

### Post by steeldriver on 2014-09-25
Have you checked "under" the other mounted filesystems (e.g. unmount /dev/md0 and see if there is still 'stuff' in /media/Raid)?

---

### Post by bgood on 2014-09-27
Thanks for the idea, checked it but virtually nothing in there so I've still got 8GB hiding somewhere :(

root@NAS:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1        30G   19G   11G  64% /
udev            1.9G   12K  1.9G   1% /dev
tmpfs           383M  1.4M  382M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
/dev/sdf1        29G   11G   17G  39% /media/DTMICRO

root@NAS:~$ du -ch /media/Raid/
104K    /media/Raid/Crashplan/618157676359091576/cpbf0000000000000000000
136K    /media/Raid/Crashplan/618157676359091576
140K    /media/Raid/Crashplan
144K    /media/Raid/
144K    total

---

### Post by bgood on 2014-10-18
If anybody else has any ideas on this it would be appreciated, don't really want to have to reinstall the system if I can avoid it, that seems to be the only solution at the minute :(

---

### Post by TheFu on 2014-10-19
> **bgood said:**
> If anybody else has any ideas on this it would be appreciated, don't really want to have to reinstall the system if I can avoid it, that seems to be the only solution at the minute :(

No need to reinstall - just use fsarchive to create a backup then wipe the partition and restore on top. Anything you can't see - usually  hidden under a mount - will be gone.

Or you can use the backup/restore method that I use (and have been using for many years).  [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) - don't use the dd or gparted "clone" method. Those won't do what you seek.

---

### Post by bgood on 2014-10-21
> **TheFu said:**
> No need to reinstall - just use fsarchive to create a backup then wipe the partition and restore on top. Anything you can't see - usually  hidden under a mount - will be gone.

Or you can use the backup/restore method that I use (and have been using for many years).  [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) - don't use the dd or gparted "clone" method. Those won't do what you seek.

Not come across fsarchive so will have a read up on that and the how to looks interesting too, thanks.

---

