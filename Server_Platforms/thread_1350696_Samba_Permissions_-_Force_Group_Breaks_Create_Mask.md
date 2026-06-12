---
title: "Samba Permissions - Force Group Breaks Create Mask"
date: 2009-12-09
forum: Server Platforms
---

### Post by t3kn0lu5t on 2009-12-09
I'm attempting to set up a samba share on my Ubuntu 8.04 LTS box, to be consumed by my mac and windows clients.

I've created a 'samba' group and added my linux users to them, gave them samba passwords, I can connect and place files, everything is peachy except the permissions.

BTW, the default home share has been completely removed to ensure it's not conflicting.

```

[archive]
path = /home/archive
read only = no
guest ok = yes
browseable = yes
create mode = 0664
directory mode = 0775
force group = samba

```

The goal is to have it readable by guests, full control for samba users.  When a non-guest user places a file in the archive share, it has the correct group of 'samba', but the permissions are 644 instead of the intended 664.  

I've tried changing the create mode and directory mode to create mask and directory mask, and every combination with the force word in front of them.

I'm at a loss for why this isn't working, any help is appreciated.

Posting my entire smb.conf:
```

[global]
 workgroup = EXAMPLE
 server string = %h
 map to guest = Bad User
 obey pam restrictions = Yes
 passdb backend = tdbsam
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
 invalid users = root
 force create mode = 0664
 force directory mode = 0775

[printers]
 comment = All Printers
 path = /var/spool/samba
 create mask = 0700
 printable = Yes
 browseable = No

[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers

[archive]
 path = /home/archive
 force group = samba
 read only = No
 create mask = 0664
 directory mask = 0775

[server_backups]
 path = /home/server_backups
 force group = samba
 read only = No
 create mask = 0664
 directory mask = 0775

```

Thanks,

---

### Post by munky99999 on 2009-12-09
[archive]
path = /home/archive
read only = no
guest ok = yes
browseable = yes
create mode = 0664
directory mode = 0775
[COLOR="SeaGreen"]force user = samba[/COLOR]
force group = samba

or whatever user.

Since you are practically giving anyone and everyone the reigns. Should pretty much do the job.

---

### Post by t3kn0lu5t on 2009-12-09
Thanks Munky,

That certainly did what it was supposed to, the file placed on the server now has both the group and the user as 'samba', but the permissions are still wrong.

I have a hunch this is because I'm using a mac to transfer the file there, and the permissions on the file I'm trying to transfer are the same as the resulting incorrect permissions on the server. Although, I would have thought that the force create mode would have taken care of that...

Here's the interesting bit:  If I don't force the group, or user, then the force create mode works!  

Unfortunately I need the group bit.

---

### Post by munky99999 on 2009-12-09
> That certainly did what it was supposed to, the file placed on the server now has both the group and the user as 'samba', but the permissions are still wrong.

[archive]
path = /home/archive
read only = no
guest ok = yes
browseable = yes
[COLOR="Red"]create mask = 0664[/COLOR]
directory mode = 0775
force user = samba
force group = samba


Create mode is wrong i think. The syntax i believe is create mask.

Also if the permissions are wrong. Perhaps change the 664 to 775?

I might be misunderstanding what's wrong.

---

