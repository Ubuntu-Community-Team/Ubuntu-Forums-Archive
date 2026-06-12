---
title: "samba permissions issue. access denied to group"
date: 2015-04-16
forum: Server Platforms
---

### Post by azharahs on 2015-04-16
Good day,

I'm having an odd issue with permissions on my samba server, running on Ubuntu Server x64 14.04

The unix permissions on the folder and subfolders are 750, where files are set to 640.  The owner and group of everything in the shared folder is adam:sambashare

The unix accounts for these users can access the files and folders normally via CLI. The "adam" account can read and write to the share as expected, however the members of the "sambashare group" are unable to access any files, even though the samba server successfully authenticates them.

example:

```

wdtv@server:/raid/storage$ smbclient \\\\server\\storage -U wdtv
Enter wdtv's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*
smb: \> dir
NT_STATUS_ACCESS_DENIED listing \*
smb: \> cd Incoming
cd \Incoming\: NT_STATUS_ACCESS_DENIED
smb: \> dir
NT_STATUS_ACCESS_DENIED listing \*
smb: \> exit
wdtv@server:/raid/storage$ 

```

So far, the only solution I've found is to change the folder/file permissions to 755 and 644 respectively, though I'd prefer not to have the "others" permissions there if I can avoid it.

Here's my smb.conf.  What am I doing wrong?

Thanks in advance for any advice!



```

[global]
        preferred master = yes
        idmap config * : backend = tdb
        unix password sync = yes
        interfaces = eth0
        socket options = TCP_NODELAY
        map to guest = never
        passwd program = /usr/bin/passwd %u
        wins support = true
        security = user
        obey pam restrictions = Yes
        protocol = NT1
        max log size = 1000
        server string = %h (Samba, Ubuntu)
        debug level = 10
        unix extensions = No
        keepalive = 30
        dns proxy = No
        os level = 90
        log file = /var/log/samba/log.%m
        pam password change = Yes
        encrypt passwords = yes
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        server max protocol = NT1
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        winbind use default domain = yes
        usershare allow guests = Yes
        winbind trusted domains only = yes

# Share directives valid for all shares:

        allow hosts = 10.1.0.0/16
        deny hosts = 10.1.0.1
        hide files = /desktop.ini/$RECYCLE.BIN/
        read only = no

# Share Definitions

[Storage]
        comment = Raid Volume
        path = /raid/storage
        valid users = adam, @sambashare

[Adam]
        comment = Adam's ****
        path = /raid/adam
        valid users = adam


```

---

### Post by azharahs on 2015-04-16
Problem solved.

The issue was caused by the mapping between Windows and Unix groups.  The Windows users were authenticating with a group name of "Users", whereas Ubuntu was expecting sambashare.

I used the "net groupmap" command to delete the existing mapping for the sambashare group, and remap it to the Windows group as follows"

```

root@server:/raid/storage# net groupmap delete ntgroup=sambashare
Sucessfully removed sambashare from the mapping db
root@server:/raid/storage# net groupmap add ntgroup="Users" unixgroup=sambashare
No rid or sid specified, choosing a RID
Got RID 1003
Successfully added group Users to the mapping db as a domain group
root@server:/raid/storage# net groupmap list
Users (S-1-5-21-2692014221-2850350512-3464132002-1003) -> sambashare

```

---

