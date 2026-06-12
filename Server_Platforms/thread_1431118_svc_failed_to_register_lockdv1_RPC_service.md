---
title: "svc: failed to register lockdv1 RPC service"
date: 2010-03-16
forum: Server Platforms
---

### Post by stek_87 on 2010-03-16
I am running an NFS server (Ubuntu 9.10 x64) and getting this in my /var/log/syslog after a restart of nfs-kernel-server restart.

Is this something to worry about or not?
I googled this for about 30 mins, and all people that are saying anything about this are experiencing serious issues with the NFS server. But I am not, the NFS server seems to work properly...


Mar 16 13:17:51 ubuntunfs mountd[9508]: Caught signal 15, un-registering and exiting.
Mar 16 13:17:51 ubuntunfs kernel: [356924.662246] nfsd: last server has exited, flushing export cache
Mar 16 13:17:53 ubuntunfs kernel: [356925.916891] svc: failed to register lockdv1 RPC service (errno 97).
Mar 16 13:17:53 ubuntunfs kernel: [356925.918142] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 16 13:17:53 ubuntunfs kernel: [356925.918168] NFSD: starting 90-second grace period


rgds
/S

---

### Post by Nodd on 2010-03-17
I'm seeing the the 'svc:failed' messages trying to set up NFS right now on 32bit 9.10 

From dmesg

[1969055.314784] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[1969056.291723] svc: failed to register lockdv1 RPC service (errno 97).
[1969056.295021] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[1969056.295105] NFSD: starting 90-second grace period
[1969532.188800] nfsd: last server has exited, flushing export cache
[1969534.411003] svc: failed to register lockdv1 RPC service (errno 97).
[1969534.414250] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[1969534.414311] NFSD: starting 90-second grace period


If I figure out what the problem is ,  I will post back here. Good luck!

---

### Post by stek_87 on 2010-03-17
Oh, okay..

Does the NFS-server work properly besides this log entry?
I'm running mdadm raid-5, and XFS as filesystem for the NFS share.
This comes up only when I start the NFS service. While running there are no error regarded to NFS in syslog.

(I saw some place when I googled around that someone else also was running XFS with this issue..)

/S

---

### Post by Nodd on 2010-03-17
As far as "svc failed" message goes , this is relevant  ( even if it doesn't explain much ! )
[http://osdir.com/ml/linux-kernel/2009-05/msg04317.html](http://osdir.com/ml/linux-kernel/2009-05/msg04317.html)
As with stek_87 , my NFS service seems to be working ok , so I'm gonna put this issue to one side for the time being.

---

### Post by stek_87 on 2010-03-17
I think I have got the solution...

(the solution is to disable ipv6)

open /boot/grub/menu.lst with a text editor

edit the line:
```
kernel          /boot/vmlinuz-2.6.31-20-server root=/dev/md1 ro quiet splash
```
to this:
```
kernel          /boot/vmlinuz-2.6.31-20-server root=/dev/md1 ro quiet splash ipv6.disable=1
```

Then run
```
sudo update-grub
```

and reboot..

Now when I restart the nfs-kernel-server no error gets logged..

/S

---

### Post by CHaoSlayeR on 2010-03-19
Default kernel boot options usually go into /etc/default/grub rather than directly into /boot/...

Makes upgrading easier and also applies to new kernels.

---

### Post by smo0th on 2010-11-30
thanks stek_87 and CHaoSlayeR for the info

---

### Post by smo0th on 2010-11-30
so... in my case it was an AllowUsers line into /etc/ssh/sshd_config, I had to modify /etc/ssh/sshd_config and add AllowUsers ubuntu and then it booted :D

---

### Post by www.rzr.online.fr on 2011-10-22
got that message too on a NFS client : laptop lenovo g470 running debian

(my NFS server is a nas running unfs3) 


Disabling ipv6 looks more like a workaround that a fix, is that issue reported on bug trackers ?

-- 
[http://rzr.online.fr/q/dmesg](http://rzr.online.fr/q/dmesg)

---

### Post by stek_87 on 2011-10-24
I have not reported a bug.
/S

---

