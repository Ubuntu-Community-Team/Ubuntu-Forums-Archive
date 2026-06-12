---
title: "Boot time too long when NAS not connected"
date: 2019-10-03
forum: Server Platforms
---

### Post by Frantic_Earthling on 2019-10-03
When I start my Intel NUC and my NAS is not connected to the netword (is switched off), booting Ubuntu takes well over one minute.

When my NAS is connected, booting takes about 10 secs after which my NAS is recognised and mounted.

It is the same with my Asus laptop.

Both are in dual boot Win10/Ubuntu 18.04 LTS.

Following are the two entries I am using in fstab :

192.168.1.30:/volume1/photo /media/Chloe_Photos nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.30:/volume1/Archives /media/Chloe_Archives nfs rsize=8192,wsize=8192,timeo=14,intr

Any ideas what I should modify for both my computers to recognise faster that no NAS is connected?

Should I add e.g. "retry=0" to both these entries?

---

### Post by TheFu on 2019-10-03
```
192.168.1.30:/volume1/photo /media/Chloe_Photos nfs    _netdev,timeo=20,intr,async     0    0
192.168.1.30:/volume1/Archives /media/Chloe_Archives nfs    _netdev,timeo=20,intr,async  0    0
```

Mounts in the fstab require 6 columns.  Leaving off the last two is bad.

From the manpage:
```
the  client  and  server negotiate  the  largest  rsize  value that they can both
support.
```
No need to specify any of those values, unless the NFS server is broken.

I use **autofs** for all NFS mounts, not the fstab. That way, the mounts only happen when the client actually requests access to the NFS storage.  The options available are in the manpages for fstab, mount, mount.nfs.  The _netdev option should tell the OS not to wait for the storage to be available, in theory.
```
       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).

```  It won't help if the network is up, but the NFS server isn't.

---

### Post by Frantic_Earthling on 2019-10-04
Many thanks for your answer and suggestion.
However, when my NAS is switched off, boot time remains exactly the same: too long :(

---

### Post by slickymaster on 2019-10-04
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2019-10-04
> **Frantic_Earthling said:**
> Many thanks for your answer and suggestion.
However, when my NAS is switched off, boot time remains exactly the same: too long :(

Autofs is the answer then.

NAS should be on first, always.  I leave all my storage servers on 24/7/366 with the drives spinning. I think spinning down drives does more damage than keeping them going and hot all the time.  There are a few 12 yr old HDDs here, still working.  1 failed from 2012 a few days ago after my UPS battery died and a power outage happened.  I see that the OS disk on a box that has been running since 2010 has a few relocated sectors, so it needs to be replaced.  It is on a different UPS which didn't have any power issues, well, not in the last 2+ yrs since the batteries on that other UPS needed replacements.

---

### Post by Frantic_Earthling on 2019-10-05
Thanks again for your help. 

I eventually settled for "nofail".
This was suggested to me by a fellow Linux user.
"no fail" did the trick.

However, I stuck to the mount entries you suggested:

```
192.168.1.30:/volume1/photo /media/Chloe_Photos nfs    _netdev,nofail,timeo=20,intr,async     0    0
192.168.1.30:/volume1/Archives /media/Chloe_Archives nfs    _netdev,nofail,timeo=20,intr,async  0    0
```

I still prefer to switch off my NAS most of the time although I understand your recommendation to leave it on all the time

---

