---
title: "Samba PDC user domain is servermachine name"
date: 2009-05-08
forum: Server Platforms
---

### Post by MetalHannes on 2009-05-08
Hello,
Upon upgrading from ubuntu server 8.10 to 9.04 the LDAP database broke and i wasn't able to recover it from the BDB files i have backed up.

This is why i decided to move back to tdbsam as the user database.

All worked well, but when the users now log on (active directory) the profile is messed up.
The keyboard always switches back to english, outlook doesn't start and the left-side of the menu is gone.

I found out that the whole user profile is being copied to the computer and savedunder "documents and settings" as username.sambaserver (sambaserver is the name of the machine samba is running on)
but i added the computers (after moving them again to the "new" workgroup) to the workgroup: WORKGROUP

when logging on the domain is defined as WORKGROUP but when i try to change the computer name via My Computer-> settings -> Computername -> network name when i have t enter a username password and Domain the username is correct but the Domain defaults to SAMBASERVER.

my smb.conf:
```
[global]
        log file = /var/log/samba/log.%m
        map hidden = no
        passwd chat = *New*password* %n\n *Retype*new*password* %n\n all*authentication*tokens*updated*
        admin users = sysadmin, root
        socket options = TCP_NODELAY
        obey pam restrictions = no
        logon drive = U:
        domain master = yes
        encrypt passwords = true
        logon home = \\%L\%U
        passdb backend = tdbsam
        dns proxy = no
        server string = %h server (Samba, Ubuntu)
        logon script = users.bat
        unix password sync = yes
        local master = yes
        workgroup = WOKRGROUP
        logon path = \\%L\%U\.msprofile
        os level = 255
        syslog = 0
        security = user
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        domain logons = yes
[homes]
        browseable = no
        writeable = yes
        printable = no
        store dos attributes = Yes
        create mask = 0600
        directory mask = 0700
        hide dot files = no
        comment = Home Directories
        inherit acls = Yes
[netlogon]
        comment = The domain logon service
        path = /netlogon/
        public = no
        writeable = no
        browsable = no
[profiles]
   comment = Users profiles
   path = /home/%S
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700
   read only = no
   store dos attributes = yes
[Server]
        writeable = yes
        create mode = 775
        path = /raidserver/
        directory mode = 775
[user]
        revalidate = yes
        browseable = no
        valid users = sysadmin
        writeable = yes
        path = /home
```

The only thing i found that someone ran into the same problem and solved it by setting domain masters = no. But the samba manpages state that this is only fpr BDCs not PDCs.

Thank you very much

Hannes

/edit: I just found out typing the command "net getlocalsid" outputs: SID for domain SAMBASERVER is: and then the sid
the command "net gelocalsid WORKGROUP" outputs: SID for domain WORKGROUP: and the SID
"net getdomainsid" outputs:
SID for local machine SAMBASERVER is: 
SID for domain WORKGROUP is: 

if thats of any importance

---

