---
title: "Samba AD and groups"
date: 2019-03-21
forum: Server Platforms
---

### Post by elcid91 on 2019-03-21
Not entirely certain if this is where I ask this question but if not please direct me to the appropriate forum.

I  have set up a simple Samba server using Samba as a Active Directory.  All seems to be running ok until I configure the shares.  Using samba-tool Ihave created a group "pps-hive" and a user "spsimmons" and added the user to the group.  Now I want to give the group access to a samba share; however, I am unclear on how to do this.  My Samba Configuration looks like this:

```
 # Global parameters[global]
        dns forwarder = 10.0.10.4
        netbios name = ADDC1
        realm = PREMPROVSOL.LOCAL
        server role = active directory domain controller
        workgroup = PREMPROVSOL


[netlogon]
        path = /var/lib/samba/sysvol/premprovsol.local/scripts
        read only = No


[sysvol]
        path = /var/lib/samba/sysvol
        read only = No


[Corporate]
        path=/mnt/corporate
        read only = No
        writable = yes
        guest ok = no
        create mode = 0777
        directory mode = 0777
        valid users = @PREMPROVSOL.LOCAL\\pps-hive

```
Running ```
wbinfo --group-info=PREMPROVSOL.LOCAL\\pps-hive
``` results in the following response:
```
PREMPROVSOL\pps-hive:x:3000021:
```

I successfully connected my Win10 machine to the domain; however, I am not able to connect to the share due to permissions.

I am only assuming that my smb.conf file is not correct; therefore I would like to request some assistance in properly setting things up.  Thank you.

---

