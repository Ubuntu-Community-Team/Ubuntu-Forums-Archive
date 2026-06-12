---
title: "Add samba users without system user"
date: 2008-03-22
forum: Server Platforms
---

### Post by ubernoob on 2008-03-22
I would like to add samba users without adding them as system users as well. how do i do that?

The users should have their own home folder which is only browsable by themself, so the permission there does not matter.

In addition, users logging in should have write permission to a shared folder. All files made there should have the same user and group permission. (nfsnobody:nfsnobody)

User logged in as guest should only have read permission to the shared folder.

Any tips on how to accomplish this?

Here is my smb.conf:

```

[global]
        workgroup = WORKGROUP
        server string = %h server
        netbios name = kengu
        log file = /var/log/samba/%m.log
        max log size = 1000
        syslog = 0
        security = user
        passdb backend = tdbsam
        encrypt passwords = true
        obey pam restrictions = yes
        invalid users = root
        wins support = yes
        load printers = no
        cups options = raw

[homes]
        comment = Home Directories
        browseable = no
        writable = yes
        path = /data/home/%S

[shared]
   comment = Shared. Guest can read. Users can write
   writable = no
   path = /data/shared
   public = yes
   security = share
   guest ok = yes

```

---

