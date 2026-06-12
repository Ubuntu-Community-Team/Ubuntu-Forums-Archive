---
title: "FTP Server?"
date: 2013-05-05
forum: Server Platforms
---

### Post by EmmEight on 2013-05-05
Hello.

I have been having some issues getting FTP configured properly on my server.

I have tried using proftpd and vsftpd, both have been failing and I can not figure out why.

After purging vsftpd and updating repos

```
apt-get purge vsftpd
apt-get update
```

I do a clean install

```
moose etc # apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 321 not upgraded.
Need to get 0 B/126 kB of archives.
After this operation, 352 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package vsftpd.
(Reading database ... 186500 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.3.5-3ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/1677: No space left on device
Setting up vsftpd (2.3.5-3ubuntu1) ...
vsftpd start/running, process 1742
Processing triggers for ureadahead ...

```


Then of course, try to run vsftpd

```
moose etc # vsftpd
500 OOPS: could not bind listening IPv4 socket
moose etc #
```



Can't create a socket, error with linux firewall? 

Any help would be great!!

---

### Post by tripp98 on 2013-05-05
looks like your drive is full.


/usr/bin/mandb: can't write to /var/cache/man/1677: No space left on device

do df -h and post output in thread

---

### Post by EmmEight on 2013-05-05
moose ~ # df -h
Filesystem             Size  Used Avail Use% Mounted on
/dev/sda3               19G   18G     0 100% /
udev                   976M  4.0K  976M   1% /dev
tmpfs                  394M  1.2M  393M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   985M  1.2M  984M   1% /run/shm
none                   100M   12K  100M   1% /run/user
/dev/mapper/srvr-srvr  1.8T   17G  1.7T   1% /srvr

---

### Post by LHammonds on 2013-05-06
Yep, your root file system "/" is full.  That is really bad.

Take a look in the boot folder: ** ls -l /boot/vm***

```

-rw------- 1 root root  5180864 Mar 26 14:54 vmlinuz-3.5.0-26-generic
-rw------- 1 root root  5180864 Mar 26 14:54 vmlinuz-3.5.0-27-generic
-rw------- 1 root root  5183296 Apr 24 17:04 vmlinuz-3.5.0-28-generic

```

If there are more than 2 images in there, you can purge the oldest ones with "apt-get remove"

For example, in the above list, I can remove version 26.  However, you need need to type the base part of the command and then add on the name of the file starting with the version number.

Base part of the command that does not change is: **apt-get remove linux-image-**

You then add on the image filename starting with the version number like so: **apt-get remove linux-image-[COLOR=#ff0000]3.5.0-26-generic[/COLOR]**

There are other places you can check to clean up files but /boot tends to grow over time and is easy to clean out.

**EDIT:** Other things you can do to help find out where your space is being consumed is the du (disk usage) command.  Example uses:

du -sh /
du -sh /tmp
du -sh /usr

---

