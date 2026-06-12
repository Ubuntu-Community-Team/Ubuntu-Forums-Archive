---
title: "Samba share problem with Thunderbird (and Matlab)"
date: 2009-06-10
forum: Server Platforms
---

### Post by wallsensus on 2009-06-10
I have a samba share setup on a Linux box.  My problem with it is very specific.  

My samba share will write files with full permissions 777 if i copy them over through nautilus 

But, I have a network folder in the share which contains emails.  Everyone on my network has Thunderbird setup to use view these common email folders so that we can all store emails in the same location.  When a user tries to create a new folder on the server it is created with 644 permissions.  I need it to be 777 (or at least 666).  When a user tries to create a new folder on the network share it sets the permisisons to 644 and the user is further prevented from writing to it for some reason.

The same thing happens when I try to save 'mat' files in matlab.

Doing the same things in windows with the share mapped as a network drive works fine.

Below is my smb.conf
```
 
# Samba config file created using SWAT
# from 192.168.0.114 (192.168.0.114)
# Date: 2009/06/10 10:53:51

[global]
        workgroup = WORKGROUP
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        log level = 3
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 100000
        min protocol = NT1
        os level = 255
        preferred master = Yes
        dns proxy = No
        ldap ssl = no
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        valid users = user1, user2, user3
        admin users = adminuser
        write list = @projects, user1, user2, user3
        force group = projects
        read only = No
        create mask = 0777
        force create mode = 0777
        directory mask = 0777
        force directory mode = 0777
        inherit permissions = Yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Server]
        comment = Server
        path = /SHARED

```  

the permissions of the folder /SHARED are 2777 on the host.  When it mounts on a client, its permissions are also 2777.

Does anyone have any ideas?  Thanks

---

