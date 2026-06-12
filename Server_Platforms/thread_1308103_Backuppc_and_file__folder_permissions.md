---
title: "Backuppc and file / folder permissions"
date: 2009-10-31
forum: Server Platforms
---

### Post by DrJohn999 on 2009-10-31
Ubuntu 8.04 LTS server; backuppc 3.0.0; ubuntu 9.04 client; rsyncd-type configuration.

Files and folders with owner-only permissions are denied access and not backed up. From backuppc's error log:

```
Remote[1]: rsync: opendir "/home/localuser/.mozilla-thunderbird" (in Root) failed: Permission denied (13)

```
Directory of the denied folder:
```
drwx------  4 localuser localuser  4096 2009-10-27 08:05 .mozilla
drwx------  3 localuser localuser  4096 2009-10-27 08:05 .mozilla-thunderbird
```

Files and folders with at least read-only group and all permissions are backed up. FOr example:
```
drwxr-xr-x  7 localuser localuser  4096 2009-10-28 18:01 .evolution
```



Client-side /etc/rsyncd.conf:
```
uid = nobody
gid = nogroup
use chroot = true
max connections = 0
log format = %h %o %f %l %b
log file = /var/log/rsyncd.log

[Root]
	path = /
	comment = Full Backup
	read only = false
	auth users = myusername
	secrets file = /etc/rsyncd.secrets
	hosts allow <server>
	hosts deny *


```

Server-side (client.pl)
```
$Conf{RsyncShareName} = [
 'Root'
];
$Conf{RsyncdPasswd} = 'hidden';
$Conf{BackupFilesExclude} = {
  '*' => [
    '/proc',
    '/sys',
    '/tmp',
    '/media',
    '/var/tmp',
    '/var/cache',
    '/var/run',
    '/var/lock',
    '/var/spool',
    '/dev',
    '/mnt'
  ]
};

```

How do I cause backuppc to gain sufficient priviledges to copy these files? 

Thanks!

---

### Post by ViRMiN on 2009-11-01
Maybe not the best solution there is but, I have specific modules defined for backuppc to access as root:

```

[backuppc-etc]
        comment = BackupPC Connector /etc
        path = /etc
        read only = no
        write only = no
        uid = 0
        gid = 0
        hosts allow = backuppcserver
        auth users = backuppc
        secrets file = /etc/rsyncd.secrets

```

I also define a connection password in /etc/rsyncd.secrets and set ownership as 'root:root' with perms 0600:

```

backuppc:secretpassword

```

That way, even though the module's there, it requires authentication and is accessible only by the "backupserver" host on the LAN.

You can repeat the module configuration for each top-level directory you need, I have ones for /etc, /home and /root defined, and then use these in the backuppc list of rsyncd modules.

Hope that helps you get started.

---

### Post by DrJohn999 on 2009-11-01
Yes, that's all set up here but it's not the problem. This has arisen as I've moved away from all Windows machines except the server to all Ubuntu machines except one remaining Windows client. When I need to I run additional WinXP or Win7 instances in VirtualBox behind its internal DHCP/NAT ethernet ports. No need for separate backuppc hosts for these PCs, just back up the virtual HDs.

And yes, if I disable chrooting and use 'root' or '0' as the uid and gid values then the backup process does gain root privileges and it picks up all of the specified files. But, this represents a moderate security risk, particularly on the Windows machine.

I think it will be better to use a secured ssh connection to gain root rsync access for the Ubuntu systems, as described here: [http://www.howtoforge.com/linux_backuppc]("http://www.howtoforge.com/linux_backuppc").

But what about Windows? How to better secure the rsyncd setup there? Install ssh-client under Cygwin and use rsync ala the Linux clients?

---

