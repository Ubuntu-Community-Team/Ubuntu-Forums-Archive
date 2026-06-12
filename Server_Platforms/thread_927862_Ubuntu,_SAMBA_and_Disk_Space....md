---
title: "Ubuntu, SAMBA and Disk Space..."
date: 2008-09-23
forum: Server Platforms
---

### Post by Negative on 2008-09-23
Let me start by apologizing if this is in the wrong section, and by pointing out I am NOT the one doing the install I am just the problem solver.

My co-worker installed Ubuntu on a 250G HDD, fresh.  He then installed SAMBA and set the computer up to act as a server.  After some minor tweaks on his part and some minor tweaks on my part everything works wonderful.  The users and groups are found, all the computers talk to each other and can see each other (as far as I am aware), however we are having a problem with disk space.

We tried to move a folder over from a Windows machine to the server and got the disk full warning, operation aborted.

When we checked the Ubuntu disk it was reporting / was 15.5 gig and full to the brim.  The other 230+ gigs are no where to be seen.

What can I do to get the server and everything to recognize the full disk as free space?

When going through filesystem it reads all 250 gig, but when actually using it I only get the 15.5.

Ideas?

Thanks!

---

### Post by cdenley on 2008-09-23
Post this output
```

sudo fdisk -l
df -h

```

---

### Post by Negative on 2008-09-24
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b916c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         578     4642753+  83  Linux
/dev/sda2             579       30401   239553247+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris
/dev/sda6             579       28000   220267152   83  Linux
/dev/sda7           28001       29164     9349798+  82  Linux swap / Solaris

Partition table entries are not in disk order



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             209G   13G  186G   7% /
varrun                1.7G  244K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   56K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.7G   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      209G   13G  186G   7% /root/.gvfs

```

Thanks!

---

### Post by cdenley on 2008-09-24
That all looks correct to me. Your / filesystem is certainly not full.
> 
When we checked the Ubuntu disk it was reporting / was 15.5 gig and full to the brim. The other 230+ gigs are no where to be seen.

How did you do this?
> 
We tried to move a folder over from a Windows machine to the server and got the disk full warning, operation aborted.

Is the share mapped to a network drive on the windows computer? I don't think windows is aware of disk usage for network shares unless they are mapped. Did you try a linux client?

---

### Post by Negative on 2008-09-24
We saw the 15.5 full using disk analyzer. And the shared drive is not mapped.

Oh, and there are no Linux clients around.  Just the one acting as the server all the others are WinNT based.

---

### Post by cdenley on 2008-09-24
> **Negative said:**
> We saw the 15.5 full using disk analyzer. And the shared drive is not mapped.

Oh, and there are no Linux clients around.  Just the one acting as the server all the others are WinNT based.

disk analyzer? I'm not familiar with that application, but I believe it is wrong, or you are interpreting it wrong.

Did you try mapping it? I've seen windows programs that refuse to write to a share that wasn't mapped because it thought the disk was full. This is a windows/client problem, and there is nothing you can do on the server to fix it.

---

### Post by Negative on 2008-09-24
Okay I will try that.  Thanks!

---

