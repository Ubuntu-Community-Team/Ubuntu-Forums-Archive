---
title: "samba-3.x versus samba-2.x - file permissions"
date: 2006-08-10
forum: Server Platforms
---

### Post by skarg on 2006-08-10
Hello,

I recently created a ubuntu-server to replace a debian-stable server that I was using for samba in order to increase storage.  It is just a local file server on my home LAN.  Samba-3.x acts differently than samba-2.x, and I am having trouble with permissions.  

For example, I insert a compact flash card connected to a USB reader on my kubuntu workstation, and copy a file to the samba server.  The file on the CF card shows rwx------ permissions.  After it is copied to the samba server, the workstation shows/obeys the same permissions, even though my fstab file is configured to show the samba mount files as rw-rw-rw- and the samba server has some force permission settings.  

The actual samba server filesystem shows the file as rwxrw--rw-.  I have turned off unix extensions both on the samba server and turned off Linux extensions on the kubuntu workstation, but that only solved the UID/GID issue, not the permissions.  If I umount/mount the share on the workstation, the permission from /etc/fstab take effect.

How do I get samba 3.x to behave like 2.x where it would keep/report the group permissions as I force them?

Best Regards,

Steve
---------------------------------------------
from /etc/fstab on kubuntu-dapper workstation:
//vader/data /mnt/data cifs auto,rw,guest,uid=nobody,gid=users,dir_mode=02777,file_mode=0666,nosetuids,noperm,directio,noacl 0 0

from /etc/samba/smb.conf on ubuntu-server dapper:

[global]
security = share

[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        unix extensions = No
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        csc policy = disable

[data]
  comment = Common Data Directory
  path = /home/skarg/data
  force user = nobody
  force group = users
  read only = No
  create mask = 0666
  force create mode = 0666
  directory mask = 02777
  force directory mode = 02777
  inherit permissions = Yes
  guest ok = Yes

---

### Post by skarg on 2006-09-05
I finally got it working like I wanted, and thought I would post the results.

First - both were running samba 3.x, one was on debian, one on ubuntu server.

So, I just copied the /etc/samba/smb.conf file from the old server and just modifed the share names, and voila!  It was working again.

Here is the /etc/samba/smb.conf file that worked. I used the command "testparm" to show it without comments.

```

[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = lmhosts host wins bcast
        socket options = IPTOS_LOWDELAY TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
        dns proxy = No
        wins server = 192.168.0.32
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No

[cdrom]
        comment = Samba server's CD-ROM
        path = /cdrom
        guest ok = Yes
        locking = No
        preexec = /bin/mount /cdrom
        postexec = /bin/umount /cdrom

[data]
        comment = Common Data Directory
        path = /home/skarg/data
        force group = users
        read only = No
        create mask = 0666
        force create mode = 0666
        directory mask = 02777
        force directory mode = 02777
        inherit permissions = Yes
        guest ok = Yes

```

My /etc/fstab entry on the clients look like this:

```

//vader/data /mnt/data cifs auto,rw,guest,uid=nobody,gid=users,dir_mode=02777,file_mode=0666 0 0

```

Best Regards,

Steve

---

