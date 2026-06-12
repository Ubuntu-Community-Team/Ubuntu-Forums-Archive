---
title: "New Folders from OSX finder have wrong permissions"
date: 2020-08-06
forum: Server Platforms
---

### Post by gzumann on 2020-08-06
Hi guys,
I am stuck. I have enabled vfs fruit and set directory mask and force directory in my smb.conf.
Nevertheless whenever a new folder is created on the share from finder you can't rename it.
Checking its permissions it has ACL set and is set to 755 instead of 770.
You can find my smb.conf attached any ideas anyone?

Thanks for helping a newbie out.

```

[global]

min protocol = SMB2
vfs objects = fruit streams_xattr  
fruit:metadata = stream
fruit:model = MacSamba
fruit:posix_rename = yes 
fruit:veto_appledouble = no
fruit:wipe_intentionally_left_blank_rfork = yes 
fruit:delete_empty_adfiles = yes 


delete veto files = yes


   workgroup = WORKGROUP
   security = user
   server string = %h server (Samba, Ubuntu)


   log file = /var/log/samba/log.%m


   max log size = 1000


   logging = file
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server


   obey pam restrictions = no
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


   pam password change = yes


   map to guest = bad user




[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
;   read only = yes
   create mask = 0700


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


[office]
   comment =  Samba Share
   path = /srv/samba/office
   readonly = no
   browseable = yes
   writeable = yes
   guest ok = no
   create mask = 0770
   directory mask = 0770
   force group = innenhof
   force user = nobody
   force create mode = 0770
   force directory mode = 0770
 force directory security mode = 2770



```

---

### Post by gzumann on 2020-08-06
[Update]
Apparently when setting
*vfs objects =fruit*
and leaving away the *streams_xattr* parameter 
I can now rename newly created folders.
Nevertheless the folder is still created with the wrong permissions.

---

