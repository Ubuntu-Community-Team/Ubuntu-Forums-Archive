---
title: "Cant write on mounted 2nd hdd"
date: 2009-10-09
forum: Server Platforms
---

### Post by ncnbnt on 2009-10-09
Hello,

today i installed and mounted successfully a second hdd.
I mounted it in subdomains directory.
When i filezilla to the directory of subdomains i can delete-create open any folder or files.EVEN THOUGHT folders EXISTS says 

550 /subdomains: No such file or directory




HELPPP

Thanks

---

### Post by gombadi on 2009-10-09
Can you provide us with some more information please.

Can you post the output of the following commands

```

cat /etc/fstab
mount
df -h
ls -la /

```

---

### Post by ncnbnt on 2009-10-10
[SIZE=5]_**1ST COMMAND**_[/SIZE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=504515c4-3be3-4616-8258-c108b6e989b6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f92ac86a-cc03-4e38-9557-1e96d9269fc0 none            swap    sw              0       0
/dev/sdb  /var/www/vhosts/mydomain/subdomains/  ext3   defaults 0 0


[SIZE=5]_**2ND COMMAND**_[/SIZE]



/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
/dev/sdb on /var/www/vhosts/megashare.gr/subdomains type ext3 (rw)
tmpfs on /opt/psa/handlers/before-local type tmpfs (rw)
tmpfs on /opt/psa/handlers/before-queue type tmpfs (rw)
tmpfs on /opt/psa/handlers/before-remote type tmpfs (rw)
tmpfs on /opt/psa/handlers/info type tmpfs (rw)
tmpfs on /opt/psa/handlers/spool type tmpfs (rw,mode=0770,gid=31)


[SIZE=5]**_3RD COMMAND_**[/SIZE]



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  138G   15M 100% /
varrun                1.7G   88K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   40K  1.7G   1% /dev
devshm                1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G   40M  1.7G   3% /lib/modules/2.6.24-24-generic/volatile
/dev/sdb              925G  138G  741G  16% /var/www/vhosts/mydomain/subdomains
tmpfs                 1.7G     0  1.7G   0% /opt/psa/handlers/before-local
tmpfs                 1.7G     0  1.7G   0% /opt/psa/handlers/before-queue
tmpfs                 1.7G     0  1.7G   0% /opt/psa/handlers/before-remote
tmpfs                 1.7G     0  1.7G   0% /opt/psa/handlers/info
tmpfs                 1.7G     0  1.7G   0% /opt/psa/handlers/spool



[SIZE=5]_**4RD COMMAND**_[/SIZE]



total 108
drwxr-xr-x  22 root root  4096 2009-10-09 17:13 .
drwxr-xr-x  22 root root  4096 2009-10-09 17:13 ..
drwxr-xr-x   2 root root  4096 2009-07-27 16:38 backup
drwxr-xr-x   2 root root  4096 2009-06-10 12:38 bin
drwxr-xr-x   3 root root  4096 2009-10-09 17:21 boot
drwxr-xr-x  11 root root 13660 2009-10-09 18:16 dev
drwxr-xr-x  98 root root  4096 2009-10-10 09:42 etc
drwxr-xr-x   3 root root  4096 2009-06-10 19:43 home
drwxr-xr-x   2 root root  4096 2009-06-10 12:34 initrd
lrwxrwxrwx   1 root root    33 2009-06-10 12:36 initrd.img -> boot/initrd.img-2.6.24-24-generic
drwxr-xr-x  14 root root 12288 2009-09-01 14:58 lib
drwx------   2 root root 16384 2009-06-10 12:33 lost+found
drwxr-xr-x   2 root root  4096 2009-06-10 12:33 media
drwxr-xr-x   2 root root  4096 2008-04-15 05:53 mnt
drwxr-xr-x   4 root root  4096 2009-06-10 13:02 opt
dr-xr-xr-x 131 root root     0 1970-01-01 00:00 proc
drwxr-xr-x  14 root root  4096 2009-07-27 17:22 root
drwxr-xr-x   2 root root  4096 2009-09-01 14:58 sbin
drwxr-xr-x   2 root root  4096 2009-06-10 12:34 srv
drwxr-xr-x  12 root root     0 2009-10-09 18:17 sys
drwxrwxrwt   4 root root 16384 2009-10-10 16:04 tmp
drwxr-xr-x  12 root root  4096 2009-06-10 19:43 usr
drwxr-xr-x  17 root root  4096 2009-06-11 08:22 var
lrwxrwxrwx   1 root root    30 2009-06-10 12:36 vmlinuz -> boot/vmlinuz-2.6.24-24-generic


PLEASE HELPP...THANKSS

---

### Post by gombadi on 2009-10-10
> 
550 /subdomains: No such file or directory

and
> 
/dev/sdb /var/www/vhosts/mydomain/subdomains/ ext3 defaults 0 0


The actual directory is mounted on /var/www/vhosts/mydomain/subdomains but the error message just says /subdomains.

Is there some sort of mapping of requests from /subdomains to the above mount point? chroot perhaps? Are you using some sort of ftp server that has some sort of doc root set to the above mount point.

---

### Post by Vegan on 2009-10-10
I found mounting a disk deep down was a nuisance. So I tried making /disk2 and put my disk there.

Then I moved files there, pointed this and that to the mounted disk.

---

### Post by cariboo on 2009-10-11
It looks like you haven't set up a partition on dev/sdb, can you post the output of:

```
sudo fdisk -l
```

in your next post.

---

