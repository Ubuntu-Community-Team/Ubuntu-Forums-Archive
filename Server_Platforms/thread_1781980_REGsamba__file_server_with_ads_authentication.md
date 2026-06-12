---
title: "REG:samba  file server with ads authentication"
date: 2011-06-14
forum: Server Platforms
---

### Post by chinnappan on 2011-06-14
[SIZE=3]**Our system setup: windows  server domain controller 2008  **


[/SIZE]   [SIZE=3]We are installed samba   in Ubuntu 11.04, with ads authentication using winbind,   i can able to give the access restriction from Linux for windows ADS User for Linux samba share folder  , all are working fine from Linux,   

i want give the access fro domain user from MS -windows , what is the  file permission owner ,etc, any one try this concept please give me a  any document any example , kindly need full.  I hope  understand my issues.

please find our configuration in smb.conf

[global]
        workgroup = test
        realm = test.COM
        server string = %h server (Samba %v, Ubuntu)
        security = ADS
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        domain master = No
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 6000-20000
        idmap gid = 6000-20000
        template homedir = /home/test/%D/%U
        template shell = /bin/bash
        winbind separator = +
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes

[Project]
        comment = test Project Share
        path = /home/Project
        read only = No
        create mask = 02775
        directory mask = 02775
        inherit permissions = Yes
        inherit acls = Yes
        map acl inherit = Yes
        vfs objects = recycle
        recycle:exclude = *.tmp,*.TMP,*.jpeg,*.jpg,*.JPG,*.JPEG,*.avi,*.wmv,*.mpeg,*.mp3,*.inf,*.ini
        recycle:maxsize = 0
        recycle:versions = Yes
        recycle:touch = Yes
        recycle:keeptree = Yes
        recycle:repository = /Project/.samba_trash/%U

[Recycle_data]
        comment = Deleted DATA
        path = /home/Project/.samba_trash
        inherit permissions = Yes
        browseable = No
        browsable = No
#        Valid Users = @chinnappan-it
        admin users = administrator



 -chinnappan[/SIZE]

---

### Post by chinnappan on 2011-06-16
Any one help me this issues please

---

### Post by chinnappan on 2011-07-10
Any one help me . or send me the any document  for this pls

---

