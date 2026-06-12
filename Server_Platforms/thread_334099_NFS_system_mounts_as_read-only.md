---
title: "NFS system mounts as read-only"
date: 2007-01-08
forum: Server Platforms
---

### Post by liquidsunshine@gmail.com on 2007-01-08
I am currently trying to make an NFS export on my server writable by my laptop for backup purposes.

I am using Dapper (6.06) on both machines.

The relevant line in my /etc/exports on the server is as follows:
```
/mnt/hdd1/backups/ 192.168.0.0/255.255.255.0 (rw,sync,no_root_squash)
```

The relevant line in my /etc/fstab on the laptop is as follows:
```
192.168.0.101:/mnt/hdd1/backups    /media/backups   nfs   user,auto,exec,rw,hard	0	0
```

When I try to mkdir /media/backups/fish on the laptop, as user or root, it returns the following error message:
*mkdir: cannot create directory `/media/backups/fish': Read-only file system*

Why is it mounting it read-only when I explicitly tell it to write "rw" in both exports and fstab?

---

### Post by ChAoS.ct on 2007-01-08
I can write to my shared NFS partitions. My /etc/fstab is like follows:

```
sirius.univers:/home/ftp /media/ftpsirius nfs rsize=8192,wsize=8192,intr,_netdev,timeo=14 0 0
```

And in /etc/exports I have the option async and not sync. 

Good luck!

---

### Post by liquidsunshine@gmail.com on 2007-01-09
You'd think I would have learned not to make typos by now, but alas... ```
/mnt/hdd1/backups/ 192.168.0.0/255.255.255.0 (rw,sync,no_root_squash)
```
should have been 
```
/mnt/hdd1/backups/ 192.168.0.0/255.255.255.0(rw,sync,no_root_squash)
```
without a space after the hostname/ip address.  I corrected that, ran 
```
sudo exportfs -r
```
to fill in mountd on the change, and it works like a charm.  Thanks for the suggestion, though, ChAoS.ct.

---

