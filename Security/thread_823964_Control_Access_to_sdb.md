---
title: "Control Access to sdb?"
date: 2008-06-09
forum: Security
---

### Post by spike_strip on 2008-06-09
Hello All,

I just installed a new harddrive sdb. I changed the permission, and from an Access Control standpoint I am not sure if I have assigned the proper permissions to secure this new drive, in other words, anyone can do any thing to this drive.

Hear is the out put from ls -l ```
drwxrwxrwx 5 local01 root 4096 2008-06-09 11:02 sdb 
```

This drive is mounted at /media/sdb

I am local01 and no one else needs access. 

Any feed back is much appreciated.

---

### Post by reacocard on 2008-06-09
try adding umask=0077 to your mount options. That should give full permissions to the owner of sdb and no permissions to anyone else.

---

### Post by spike_strip on 2008-06-09
assume you are saying to add it to my fstab config file[?] 

This is what I have now ```
 /dev/sdb1	/media/sdb	ext3 	defaults  0	2
``` where to add?

That is exactly what I am seeking to do 

> **reacocard said:**
> no permissions to anyone else.

---

### Post by reacocard on 2008-06-10
> **spike_strip said:**
> assume you are saying to add it to my fstab config file[?] 

This is what I have now ```
 /dev/sdb1	/media/sdb	ext3 	defaults  0	2
``` where to add?

That is exactly what I am seeking to do

like this:
```
 /dev/sdb1	/media/sdb	ext3 	defaults,umask=0077  0	2
```

---

### Post by hyper_ch on 2008-06-10
what do you mean by "securing access"?

---

### Post by spike_strip on 2008-06-10
> **hyper_ch said:**
> what do you mean by "securing access"?

Well; maybe adding security threw proper access[?], to sdb. 
 
I am just not comfortable with the access right to sdb and would like to address it now!

---

### Post by spike_strip on 2008-06-10
> **reacocard said:**
> like this:
```
 /dev/sdb1	/media/sdb	ext3 	defaults,umask=0077  0	2
```

I edited my fstab file just as shown hear and sdb did not mount on reboot, and I received error w/ mount -a. However, I will do it again!

Thanks!

---

### Post by hyper_ch on 2008-06-10
I still don't understand what the problem is with the access to sdb1.

---

### Post by spike_strip on 2008-06-10
OK; this is the out-put from mount -a ```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or other error In some cases useful info is found in syslog – try dmesg | tail  or so
```

And hear is out-put from dmesg | tail ```
[42949508.140000] EXT3-fs: Unrecognized mount option "umask=0077" or missing value
```

---

### Post by hyper_ch on 2008-06-10
I don't think it's an ext3 fs.

---

### Post by spike_strip on 2008-06-10
Everyone has rwx permissions—to sdb; I am attempting to provide only access to me the owner and no access to everyone else.

Are you implying that the access is set correctly[?] hear is what it looks like ```
brw-rw---- 1 root disk 8,  17 2008-06-10 10:51 sdb1
```

---

### Post by hyper_ch on 2008-06-10
according to the error output it is not mounted becaue it's not ext3 and you try to mount it as ext3

---

### Post by spike_strip on 2008-06-10
It mounts as an ext3 when umask is not present, and I formated sdb as an ext3. 
How can I check the fs type?

When fstab is ```
/dev/sdb1       /media/sdb      ext3    defaults  0     2 
``` it mounts on boot—no error!

---

### Post by spike_strip on 2008-06-10
Using GUI-->System/Administration/Disk; it states fs type Extended 3

---

### Post by hyper_ch on 2008-06-10
check that drive with fsck

---

### Post by spike_strip on 2008-06-10
What about this out-put from mount ```
/dev/sdb1 on /media/sdb type ext3 (rw)
```

Do not know syntax for checking sdb w/ fsck...

---

### Post by spike_strip on 2008-06-10
What about this out-put from ls -l ```
/   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8559    68750136   83  Linux
/dev/sdb2            8560        8924     2931862+   5  Extended
/dev/sdb5            8560        8924     2931831   82  Linux swap / Solaris
```

---

### Post by spike_strip on 2008-06-10
Hello--

I am going to abandoned this idea and attempt to control file access permissions to sdb1 via restrictive Access Control List. Do not know how to use ACL, therefore still learning.

Thanks for the feedback!   :confused:

---

