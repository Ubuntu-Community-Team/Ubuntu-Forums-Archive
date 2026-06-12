---
title: "Samba SeDiskOperatorPrivilege required for read access"
date: 2019-01-02
forum: Server Platforms
---

### Post by duncthepunk on 2019-01-02
I have almost finished configuring a new Samba AD DC & File Server for a non-profit but I had an access problem. It seems my file server requires 'INTRANET\Domain Users' have Samba SeDiskOperatorPrivilege rights just to view the share. Before granting the privilege, the users couldn't open the share. I could make them 'Domain Admins' (which has/had SeDiskOperatorPrivilege) and it would work. I am planning to install this tomorrow and I would rather not give them SeDiskOperatorPrivilege but I will if required. Any ideas?

Tech details:
AD DC: Ubuntu 18.04.1 Server with latest Samba from apt-get (sorry I can't remember the version. I can check when onsite tomorrow)
FIle server: Ubuntu 18.04.1 Desktop (yes, shame on my for installing the GUI. It's so I can preview documents in LibreOffice if I need to restore from an offline Hyper-V checkpoint) with latest Samba.
File server is bound to above AD with Samba and hosts NTFS ACLs which are working.

---

### Post by jeremy31 on 2019-01-02
Moved to Servers

---

### Post by duncthepunk on 2019-01-02
> **jeremy31 said:**
> Moved to Servers

Thanks Jeremy. I wasn't sure as it was built with Ubuntu Desktop.

---

### Post by duncthepunk on 2019-01-03
Here is my smb.conf:
> [global]
   workgroup = INTRANET
   realm = INTRANET.COMPANY.COM
   security = ADS
   vfs objects = acl_xattr
   map acl inherit = yes
   store dos attributes = yes
   inherit permissions = yes
   inherit acls = yes
   acl_xattr:default acl style = windows
   acl_xattr:ignore system acls = yes
   ntlm auth = true
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = member server
   passdb backend = tdbsam
   obey pam restrictions = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

    idmap config * : backend = tdb
    idmap config * : range = 100000-299999
    idmap config INTRANET : backend = rid
    idmap config INTRANET : range = 10000-99999
    winbind separator = +
    winbind enum users = yes
    winbind enum groups = yes
    winbind use default domain = yes
    winbind refresh tickets = yes
    restrict anonymous = 2

[shared]
   comment = Shared data
   path = /srv/shared/data
   read only = no
   vfs objects = acl_xattr
#   force group = "Domain Users"
#   directory mask = 0770
#   force directory mode = 0770
#   create mask = 0660
#   force create mode = 0660
   nt acl support = yes
   hide unreadable = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

And my smbstatus:
> Samba version 4.7.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------
2181    duncan.----- domain users 192.168.157.21 (ipv4:192.168.157.21:57037) SMB3_11           -                    partial(AES-128-CMAC)

Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------
shared       2181    192.168.157.21 Fri Jan  4 08:33:39 2019 AEDT    -            -

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
2181         11105      DENY_NONE  0x100081    RDONLY     NONE             /srv/shared/data   Users/duncan.-----/Favorites   Fri Jan  4 08:33:57 2019
2181         11105      DENY_NONE  0x100081    RDONLY     NONE             /srv/shared/data   Users/duncan.-----/Favorites   Fri Jan  4 08:34:18 2019
2181         11105      DENY_NONE  0x100081    RDONLY     NONE             /srv/shared/data   .   Fri Jan  4 08:33:39 2019


---

