---
title: "Samba + tdbpasswd : Samba passwords syncing to unix passwords on restart"
date: 2015-03-25
forum: Server Platforms
---

### Post by daniel201 on 2015-03-25
I've got a Samba server running on 14.04.1 (Trusty Tahr).
I've already got a linux account configured on the server with a randomly generated password. I added a samba account with an easier password using:

smbpasswd -a MyUserName

Initially I can connect to the samba shares with any problem using the samba user name and password I just created. However, when smbd is restarted, the samba password gets changed to the randomly generated linux password.

My configuration looks like this:

```
[global]
        workgroup = myWorkgroupd
        server string = srvHostName.MyDomain.internal
        interfaces = lo br0
        bind interfaces only = yes
        wins support = yes
        name resolve order = wins hosts lmhosts broadcast
        dns proxy = yes
        domain master = no
        local master = yes
        preferred master = yes
        os level = 65
        log level = 3
        log file = /var/log/samba/log.%m
        max log size = 1000
        panic action = /usr/share/samba/panic-action %d
        server role = standalone server
        passdb backend = tdbsam
        map to guest = bad user
        usershare allow guests = no


[share]
        comment = Private Share
        path = /zfs/folder
        browseable = yes
        read only = no
        guest ok = no
        valid users = myUserName
        force user = myUserName
        force group = myUserName
        create mask = 0664
        directory mask = 0775



```


I haven't explicitly set-up any kind of password synchronization. Is this expected behaviour?
Thanks

---

### Post by bab1 on 2015-03-25
> **daniel201 said:**
> I've got a Samba server running on 14.04.1 (Trusty Tahr).
I've already got a linux account configured on the server with a randomly generated password. I added a samba account with an easier password using:

smbpasswd -a MyUserName

Initially I can connect to the samba shares with any problem using the samba user name and password I just created. However, when smbd is restarted, the samba password gets changed to the randomly generated linux password.

My configuration looks like this:

```
[global]
        workgroup = myWorkgroupd
        server string = srvHostName.MyDomain.internal
        interfaces = lo br0
        bind interfaces only = yes
        wins support = yes
        name resolve order = wins hosts lmhosts broadcast
        dns proxy = yes
        domain master = no
        local master = yes
        preferred master = yes
        os level = 65
        log level = 3
        log file = /var/log/samba/log.%m
        max log size = 1000
        panic action = /usr/share/samba/panic-action %d
        server role = standalone server
        passdb backend = tdbsam
        map to guest = bad user
        usershare allow guests = no


[share]
        comment = Private Share
        path = /zfs/folder
        browseable = yes
        read only = no
        guest ok = no
        valid users = myUserName
        force user = myUserName
        force group = myUserName
        create mask = 0664
        directory mask = 0775



```


I haven't explicitly set-up any kind of password synchronization. Is this expected behaviour?
Thanks

It is the default behavior.  The sync happens because the libpam-smbpass package.  If you don't want the users logging into the Linux server use /bin/false as the login shell.  Without a working shell the user can't login.

Edit:  You can also create users with no home directory if you want.

---

