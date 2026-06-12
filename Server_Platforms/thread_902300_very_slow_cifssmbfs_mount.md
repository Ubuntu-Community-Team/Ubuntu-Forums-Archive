---
title: "very slow cifs/smbfs mount"
date: 2008-08-27
forum: Server Platforms
---

### Post by lupus7 on 2008-08-27
hi
I've mounted some file server to ubuntu with cifs (and afterwards with smbfs), but traffic goes very slow (relative to other CentOS machines).
on ubuntu server:
cat /etc/fstab:
//192.168.22.77/afs /afs   cifs  user=Guest,password=noperm 0 0

on file server (CentOS):
from smb.conf:
[qfs]
comment = 
path = /afs
guest ok = yes
browseable = yes
create mask = 0600
directory mask = 0700
read only = no
public = yes

From all other machines with CentOS (with exactly same mounting)
 traffic flows perfectly. I've checked with iperf between ubuntu and samba server and found that there's no delay in the network, so problem is with cifs/smbfs on ubuntu only.
Any help will be appreciated.

---

### Post by cdenley on 2008-08-27
I'm guessing it has to do with different kernel versions. What is this output?
```
lspci|grep Ethernet
```
It would be interesting to see if you experience the same problem with dapper.

---

### Post by lupus7 on 2008-08-27
Linux 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64 GNU/Linux

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
03:01.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)

Connections mostly go over D-Link

---

### Post by cdenley on 2008-08-27
I think that D-link adapter uses the r8169 driver, same as my Linksys gigabit cards.
```

dmesg|grep Eth

```
I have had the same issue since gutsy. I fixed it by getting the driver from linksys to compile, but never got it to compile in hardy. I wonder if the problem only happens when there are two identical cards installed.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/161778](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/161778)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159417](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159417)

I think the problem must be with the kernel module. The reason CentOS works is because it uses an older linux kernel with a different version of the module.

---

### Post by cdenley on 2008-08-27
Removing one of my cards didn't help.

Some sample transfer rates using samba
2605056 bytes (2.6 MB) copied, 7.79885 s, 334 kB/s
10485760 bytes (10 MB) copied, 13.7668 s, 762 kB/s
10485760 bytes (10 MB) copied, 31.9447 s, 328 kB/s

SFTP is significantly faster
10485760 bytes (10 MB) copied, 2.47663 s, 4.2 MB/s

This is over gigabit ethernet!

---

### Post by lupus7 on 2008-08-28
Seems that I have similar problem..
I use hardy now, and it's still doesn't work properly
Is there some workaround for this problem? Maybe some old kernel&modules is not affected?

---

### Post by cdenley on 2008-08-28
> **lupus7 said:**
> Seems that I have similar problem..
I use hardy now, and it's still doesn't work properly
Is there some workaround for this problem? Maybe some old kernel&modules is not affected?

I think an old kernel would do the trick, but there isn't one in the repos for hardy. You said CentOS worked, right? I think that uses an older kernel. You could also use a different driver/module, if there is one available. I couldn't find one for the D-link DGE-528T on the D-link website, but they provide linux drivers.

---

### Post by cdenley on 2008-08-28
I compiled/installed the Linksys EG1032v3 driver,blacklisted r8169, and now samba works as expected
> 10485760 bytes (10 MB) copied, 0.885956 s, 11.8 MB/s
The only problem with this workaround is I have do reinstall the driver every time I install a new kernel.

Good luck finding and compiling a driver that works.

---

### Post by cdenley on 2008-08-29
It seems to be fixed in the intrepid kernel, which seems to work in hardy (until I start google earth).

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-2-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-2-generic)

edit: Actually, I just noticed sound isn't working. I guess I will have to stick with the Linksys driver. If they don't fix this in hardy, I guess I will have to upgrade when intrepid is released.

---

