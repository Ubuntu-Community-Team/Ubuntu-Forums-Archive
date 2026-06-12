---
title: "lessen security on certain actions"
date: 2009-12-24
forum: Security
---

### Post by kainalu on 2009-12-24
I noticed that with the newer versions of Ubuntu, there has been a tightening of security and how many things require a password. Is there a way to selectively lower security on certain actions?

For instance:

I do not want to enter a password to access my non-Ubuntu partitions (NTFS and such), currently they remain unmounted at boot and require a password to operate.

I do not want to enter a password (this one comes up as the default keyring) to access my Mobile Broadband device when booting.

Is there a system security policy editor to just go through and lessen/tighten security as wanted/needed?

Thanks!

--Kainalu

---

### Post by liztrd on 2009-12-25
PolicyKit?  usability always conflict to security ........ before you deliberately "lessen" the security ,you must have some good reason to do that

---

### Post by q.dinar on 2009-12-25
for partitions you should edit fstab, add:
/dev/sdb7    /mnt/sdb7    ntfs    defaults,umask=007,gid=46     0       0
for fat32:
/dev/sdb8    /mnt/sdb8    vfat     defaults,umask=007,iocharset=utf8,gid=46,rw 0 0
or same but
UUID=1f6631c6-7ad1-4dc4-ad70-489412ac9764 instead of "/dev/sdb8" , that code you can see as folder name when partition is mounted as you mount it. you should create folders /mnt/sdb8 or with name as you want, and then run command "sudo mount -a" in terminal.

17:35 utc+3 : you can see all that codes mounting all partitions and then looking /etc/mtab .
but i have understood, what you say would be other way : mount not automatically , just do not ask password... for that some code should run that "mount"s as root... but there is not possible to mark script to always run as root in linux, as i know...
18:07 utc+3 : hm may be this does not work in ubuntu 9.10 ...

---

### Post by kainalu on 2009-12-25
ok Thanks for the info on the partitions. I actually knew that at some point, and had forgot. Been a long time since I had to set up anything in fstab, lol.

I looked in policykit, but it either does not have the settings I need or I dont know what Im looking at.

---

