---
title: "cannot share folders in samba"
date: 2016-04-22
forum: Server Platforms
---

### Post by pouldney on 2016-04-22
I cannot share folders in samba
 Ubuntu 14,04    3.13.0-85-generic
 This perhaps happened after last update
  Samba share was working and i did not change anything in samba

      Message when trying to share folder in Nautilus
```
Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.

$ sudo net usershare info --long
WARNING: Ignoring invalid value 'share' for parameter 'security'
Can't load /etc/samba/smb.conf - run testparm to debug it


$ sudo testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.
```


    But the smb.conf does exist
```
$ ls -l /etc/samba/smb.conf
-rw-r--r-- 1 root root 9283 Apr 22 12:09 /etc/samba/smb.conf
```

 I tried sudo apt-get --reinstall install samba-common
 I tried different saved smb.conf files

 It looks like smb.conf exists but samba commands cannot access it for some reason

   Any ideas

---

### Post by pouldney on 2016-04-23
I copied /usr/share/samba/smb.conf  to /etc/samba/  to replace my smb.conf file
    Now testparm -s  works
        So there is something in my smb.conf file  samba does not like
   I will have to modify it.

---

### Post by slickymaster on 2016-04-23
*Thread moved to **Server Platforms**.*

---

