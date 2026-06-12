---
title: "Samba shares not accessible to users and groups"
date: 2018-01-30
forum: Server Platforms
---

### Post by mdutchmdutch on 2018-01-30
[COLOR=#111111][FONT=Ubuntu]We moved up from a 3.x NT-type Samba server and built a new AD server using the SambaWiki, methodically making sure each step and test worked correctly. It's fine in administrator or Domain Admin mode, but none of the other users have share access, even to their home directory. (Note, they do have **netlogon** access.) [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Win7 and XP workstations join the domain just fine. Users can log in. Smba shares do not have access. Below is a truncated smb.conf file, showing one share "APP"
[/FONT][/COLOR]
```
# Global parameters
[global]
    workgroup = INT
    realm = INT.JINGLES.COM
    server role = active directory domain controller
    security = USER
    passdb backend = samba_dsdb
    template homedir = /samba/home/%U
    template shell = /bin/bash
    dns forwarder = 8.8.8.8
    rpc_server:tcpip = no
    rpc_daemon:spoolssd = embedded
    rpc_server:spoolss = embedded
    rpc_server:winreg = embedded
    rpc_server:ntsvcs = embedded
    rpc_server:eventlog = embedded
    rpc_server:srvsvc = embedded
    rpc_server:svcctl = embedded
    rpc_server:default = external
    winbindd:use external pipes = true
    idmap config * : backend = tdb
    map archive = No
    map readonly = no
    store dos attributes = Yes
    vfs objects = dfs_samba4 acl_xattr

[netlogon]
    path = /var/lib/samba/sysvol/int.jingles.com/scripts
    read only = No

[sysvol]
    path = /var/lib/samba/sysvol
    read only = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    write list = root @lpadmin

[app]
    comment = "Applications"
    path = /samba/app
    read only = No
```

[COLOR=#111111][FONT=Ubuntu]The permissions are set for SYSTEM, Domain Admins, and JAM_valid_user (all employees) My personal login (mark) is a member of JAM_valid_user but cannot access the share. Here's the ls followed by the ACL settings. (FYI, though not highlighted, JAM_valid_user has all share permissions set, and Full Control in Security settings.[/FONT][/COLOR]

[FONT=lucida console]**drwxrwx---+ 13 root INT\domain admins   4096 Aug 10  2015 app**[/FONT]
[COLOR=#111111][FONT=Ubuntu][B]
[IMG]http://www.jingles.com/app_permissions.jpg[/IMG]

krb5.conf:[/B][/FONT][/COLOR]
```
[libdefaults]   
    default_realm = INT.JINGLES.COM
    dns_lookup_realm = false    
    dns_lookup_kdc = true
```

[COLOR=#111111][FONT=Ubuntu]I'm a bit at a loss on how to proceed, I've been hammering at this for a week, and am currently having to put all employees into the Domain Admins group for access. Why don't they have access as members of JAM_valid_user group?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks, --Mark / mdutchmdutch[/FONT][/COLOR]

---

### Post by volkswagner on 2018-02-02
Can you provide the output of:
```
getfacl /samba/app
```

---

