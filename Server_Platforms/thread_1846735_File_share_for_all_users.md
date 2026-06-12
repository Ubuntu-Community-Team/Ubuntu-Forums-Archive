---
title: "File share for all users"
date: 2011-09-19
forum: Server Platforms
---

### Post by DRouleau on 2011-09-19
11.04 Server.  I'm trying to set up a file share on my windows network (NT 4.0, oh yeah we are up to date here) :lolflag:  We are actually moving to 2008 but still need to get this to work before the move (I'm sure I'll be re-asking this question once I get access to another server for our new network).  Anyways, how can I get my Ubuntu server to recogonize members of my windows domain/workgroup?  I made the changes in smb.conf from this ([https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)) and obviously no luck.  I can view the share folder and open it (from windows), but I can't add anything to it so it's obviously permissions based.  The last time I had to do this was about 12 months ago with our CentOS Server and I remember that was a pain (still looking for my notes).
Thanks in advance!!

---

### Post by DRouleau on 2011-09-19
At this point I'd be happy if one use could connect from windows and add a folder or file to the share, any ideas?  I can view the empty directory, just can't do anything with it...

---

### Post by Morbius1 on 2011-09-19
I usually don't respond in the "Server" section of the forums because it's beyond my pay grade but there does seem to be a step missing from that HowTo. 

The permissions on the shared folder have to be in sync with the authorization specified in the share definition so somewhere in this process you need to allow Linux "others" to have write access so a Samba "guest" can write:
```
sudo chmod 0777 /path/to/shared/folder
```

---

### Post by DRouleau on 2011-09-19
This is the smb.conf file... not sure what else I can do?

[global]
        workgroup = THOMAS
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[share]
        comment = Ubuntu File Server Share
        path = /srv/samba/share
        read only = No
        create mask = 0755
        guest ok = Yes

---

### Post by DRouleau on 2011-09-19
I knew it was something stupid... thanks :D

---

