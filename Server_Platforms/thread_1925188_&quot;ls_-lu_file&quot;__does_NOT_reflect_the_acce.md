---
title: "&quot;ls -lu file&quot;  does NOT reflect the access time !!!"
date: 2012-02-14
forum: Server Platforms
---

### Post by dchen on 2012-02-14
Not sure if this is the broken filesystem in Ubuntu 11.10 server or something else ??!! I guess it's definitely the filesys problem in 11.10 server! The access time NOT updated!  The first access time displayed correctly, but the later times of access display the SAME first access time! 
Here is how to reproduce:


admin@server:/tmp$ vi xxpp
admin@server:/tmp$ ls -l xxpp
-rw-rw-r-- 1 admin admin 37 2012-02-14 00:55 xxpp
admin@server:/tmp$ date[/B]
Tue Feb 14 00:55:57 PST 2012
admin@server:/tmp$ date
**Tue Feb 14 00:56:20 PST 2012**
admin@server:/tmp$ **cat xxpp**
sjdkljsaldjlsadlas
jdshadlsajdlsajld
admin@server:/tmp$ ls -lu xxpp
-rw-rw-r-- 1 admin admin 37 **2012-02-14 00:56** xxpp
admin@server:/tmp$ date
Tue Feb 14 00:56:53 PST 2012
admin@server:/tmp$ date
Tue Feb 14 00:58:05 PST 2012
admin@server:/tmp$ **cat xxpp**
sjdkljsaldjlsadlas
jdshadlsajdlsajld
admin@server:/tmp$ ls -lu xxpp
-rw-rw-r-- 1 admin admin 37 **2012-02-14 00:56** xxpp
admin@server:/tmp$ 

I was so frustrated about the problem of starting up the dovecot server, it failed with the following message:

Feb 14 00:42:46 server kernel: [   22.116616] init: dovecot main process (1262) terminated with status 89

I checked the /etc/dovecot/dovecot.conf file, it showed the OLD access time, it looked like it has not been read:

admin@server:/etc/dovecot$ ls -lu dovecot.conf
-rw-r--r-- 1 root root 52781 2012-02-13 18:44 dovecot.conf

Anyone please shed some light?

---

### Post by Cheesemill on 2012-02-14
What are the contents of /etc/fstab?
Maybe that drive is mounted with the noatime option.

---

### Post by dchen on 2012-02-15
> **Cheesemill said:**
> What are the contents of /etc/fstab?
Maybe that drive is mounted with the noatime option.

Here is my /etc/fstab:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/server-lv_root /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/mapper/server-lv_home /home           ext4    defaults        0       2
/dev/mapper/server-lv_swap none            swap    sw              0       0

Do you know what is the default options in /etc/fstab and/or mount  in Ubuntu 11.10 server ?

---

### Post by Wayne_V on 2012-02-15
check the output of the mount command and also Linus Torvalds discussion of relatime:

[http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)

if you look at:

touch xxpp
stat xxpp
cat xxpp
stat xxpp
cat xxpp
stat xxpp

you see that atime only updates when it equal to or older than m/ctime

---

