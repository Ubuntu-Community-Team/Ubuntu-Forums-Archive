---
title: "Samba login problems after update to 14.10"
date: 2014-12-01
forum: Server Platforms
---

### Post by andriy-golovnya on 2014-12-01
Hi!

I've got a strange behavior of samba server after update from 14.04 to 14.10.

After update users have a difficulties to login from Windows PC (perhaps not only Windows)
- samba server is visible in the network and smdn and nmbd are running in server.
- after entering correct user/pass information in login window in Windows 7/8, user get rejected with error 0x800704cf (on Windows 8.1).
- logs on ubuntu side mention nothing meaningful to me.
- after I log in to ubuntu server over ssh and update user password (enter the same pass again) with smbpasswd <user> the user can login successfully and access samba share without any problems.
- after reboot of server, samba user is still logged in.
- after reboot of Windows PC the user can't login to samba server again.

Before update to 14.10 samba had worked without problems what so ever. 

What can be a problem and how can I fix it?

Thanks in advance!
-- Ag

My smb.conf:
```

[global]        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        netbios name = Vault
        server role = standalone server
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        workgroup = HOME
        os level = 20
        create mode = 777
        syslog = 0
        usershare allow guests = yes
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        directory mode = 777
        pam password change = yes
#       log level = 10
#       max log size = 1024000
#       max protocol = SMB2
        unix extensions = no


#======================= Share Definitions =======================


#[printers]
#       comment = All Printers
#       browseable = no
#       path = /var/spool/samba
#       printable = yes
#       guest ok = no
#       read only = yes
#       create mask = 0700


#[print$]
#       comment = Printer Drivers
#       path = /var/lib/samba/printers
#       browseable = yes
#       read only = yes
#       guest ok = no


[Public]
        path = /share/Public
        vfs objects = shadow_copy2
        shadow:snapdir = ../.share
        shadow:basedir = /share
        shadow:sort = desc
        follow symlinks = yes
        wide links = yes
        valid users = user1
        writeable = yes
        write list = user1
        inherit permissions = yes
        create mode = 777
        directory mode = 777

```

---

