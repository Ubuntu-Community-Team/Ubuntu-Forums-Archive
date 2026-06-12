---
title: "CIFS mounts but cannot access"
date: 2012-07-31
forum: Server Platforms
---

### Post by VanJr on 2012-07-31
We upgraded an Ubuntu server from 11.10  (x64) to 12.04 (x64). We use autofs to auto mount Windows 2008 shares when needed. The autofs mounting and access worked fine prior to the upgrade of 12.04.

Now, the mount does occur however when you attempt to access any directories we get 'cannot access <share>':

```

root@mis001:/# cd /cifs/p2388301

root@mis001:/cifs/p2388301# ls -l
total 0
drwxr-xr-x 2 root root 0 Jul 31 11:54 ADMIN$
drwxr-xr-x 2 root root 0 Jul 31 11:54 C
drwxr-xr-x 2 root root 0 Jul 31 11:54 C$
drwxr-xr-x 2 root root 0 Jul 31 11:54 D
drwxr-xr-x 2 root root 0 Jul 31 11:54 D$

root@mis001:/cifs/p2388301# cd D
-bash: cd: D: No such file or directory

root@mis001:/cifs/p2388301# ls -l
ls: cannot access D: No such file or directory
total 0
drwxr-xr-x 2 root root 0 Jul 31 11:54 ADMIN$
drwxr-xr-x 2 root root 0 Jul 31 11:54 C
drwxr-xr-x 2 root root 0 Jul 31 11:54 C$
d????????? ? ?    ?    ?            ? D
drwxr-xr-x 2 root root 0 Jul 31 11:54 D$

```Note what happened to  'D''s permissions


And if we attempt to manually mount:

```

root@mis001:/cifs# mount.cifs //p2388301/LOGS /mnt/log -o credentials=/etc/samba/auto.smb.p2388301
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

root@mis001:/cifs# ping p2388301
PING p2388301.validdomain.com (10.10.10.252) 56(84) bytes of data.
64 bytes from p2388301.validdomain.com (10.10.10.252): icmp_req=1 ttl=128 time=73.8 ms


```So, the host is accessible.

```

root@mis001:/cifs# smbclient -L p2388301 -A /etc/samba/auto.smb.p2388301
Domain=[ECI] OS=[Windows Web Server 2008 R2 7601 Service Pack 1] Server=[Windows Web Server 2008 R2 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C               Disk      
    C$              Disk      Default share
    D               Disk      
    D$              Disk      Default share
    IPC$            IPC       Remote IPC
    LOGS            Disk      
Domain=[ECI] OS=[Windows Web Server 2008 R2 7601 Service Pack 1] Server=[Windows Web Server 2008 R2 6.1]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------

```

Any suggestions?

---

### Post by LHammonds on 2012-07-31
I don't know if this applies to your scenario but I have noticed that if you do not define the host name with the same name as the Windows server, it can get grumpy when trying to connect.

For example, if the Windows server name is **srv-file** with an IP address of 10.10.10.252, it might get grumpy if you add the following to your /etc/hosts file:

10.10.10.252  **fileserver**

It may be able to resolve and ping "fileserver" to the right IP but might fail to mount if it is not called "srv-file"

LHammonds

---

### Post by VanJr on 2012-08-01
Thanks for the input.

After all the futzing around the solution was to reboot the Windows 2008 server. Frustrating.

---

### Post by LHammonds on 2012-08-01
> **VanJr said:**
> the solution was to reboot the Windows 2008 server.
OMG...I completely forgot about mentioning the Microsoft standard solution!  ](*,) lol

---

