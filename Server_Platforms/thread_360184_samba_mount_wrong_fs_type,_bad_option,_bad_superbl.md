---
title: "samba mount: wrong fs type, bad option, bad superblock"
date: 2007-02-12
forum: Server Platforms
---

### Post by epsydom12 on 2007-02-12
i have a windows share at smb://myshare and am having a problem mounting it.  I would like to have it mounted at startup.  :) Here is my fstab entry for the windows share:

```
//myshare   /mnt/myshare    smbfs   rw,user,   0 0 
```

I have made the corresponding mount point in /mnt/.

after executing a command to mount the share: 

```
mount //myshare 
```

i get this error:
```

       mount: wrong fs type, bad option, bad superblock on //myshare,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and here are the relevant entries in dmesg:
```

[17266852.184000] smbfs: mount_data version 1919251317 is not supported
[17267529.720000] smbfs: mount_data version 0 is not supported
[17267835.588000] smbfs: mount_data version 0 is not supported

```

where have i gone wrong? :confused:

---

### Post by Iowan on 2007-02-12
Have you installed **smbfs**?
```
sudo apt-get install smbfs
```

---

### Post by gumpish on 2007-02-13
I just ran into the same problem as OP and indeed I needed to install smbfs. (Kind of misleading that GNOME shows mounting SMB shares is an option in the "Connect to Server..." dialog...)

Thanks.

---

### Post by epsydom12 on 2007-02-13
that was it, thanks.

---

### Post by travisD on 2008-04-10
This is confusing, does anyone know why this isn't included in the default distribution?

I guess it's easy enough to install, once you figure out that this is the problem.  I think it would be better that this is included as part of gnome-vfs.

---

