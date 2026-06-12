---
title: "Error when try access more of one the file samba through windows 10"
date: 2019-07-18
forum: Server Platforms
---

### Post by sed_faster on 2019-07-18
Hello,

On my smb.conf I configured two directory on my samba server. I can accessed them through my Windows 10. But only I can access/mount one folder at the time. If a accessed an folder but I have already one folder access the windows 10 show this message: [https://snag.gy/UrfmZ7.jpg](https://snag.gy/UrfmZ7.jpg)
Is the limitation on windows 10 or samba?

Thanks

---

### Post by Morbius1 on 2019-07-18
Need to see how the samba server is set up. Please post the output of the following:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by sed_faster on 2019-07-20
Hello,

Thanks to your reply,
```

$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[P 1]"
Processing section "[Private]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[P 1]
    comment = Folder Server
    create mask = 0660
    directory mask = 0771
    force group = users
    path = /home/seg_1/test
    read only = No
    valid users = @users


[Private]
    comment = Private
    create mask = 0660
    directory mask = 0771
    force group = windows_admin
    path = /home/seg_1/private
    read only = No
    valid users = @windows_admin


```

And the result of the command "net usershare info --long" is: 
```

$ net online info --long
Invalid command: net online
Usage:
net rpc             Run functions using RPC transport
net rap             Run functions using RAP transport
net ads             Run functions using ADS transport
net file            Functions on remote opened files
net share           Functions on shares
net session         Manage sessions
net server          List servers in workgroup
net domain          List domains/workgroups on network
net printq          Modify printer queue
net user            Manage users
net group           Manage groups
net groupmap        Manage group mappings
net sam             Functions on the SAM database
net validate        Validate username and password
net groupmember     Modify group memberships
net admin           Execute remote command on a remote OS/2 server
net service         List/modify running services
net password        Change user password on target server
net primarytrust    Run functions related to the primary workstation trust.
net changetrustpw   Change the trust password
net changesecretpw  Change the secret password
net setauthuser     Set the winbind auth user
net getauthuser     Get the winbind auth user settings
net time            Show/set time
net lookup          Look up host names/IP addresses
net g_lock          Manipulate the global lock table
net join            Join a domain/AD
net dom             Join/unjoin (remote) machines to/from a domain/AD
net cache           Operate on the cache tdb file
net getlocalsid     Get the SID for the local domain
net setlocalsid     Set the SID for the local domain
net setdomainsid    Set domain SID on member servers
net getdomainsid    Get domain SID on member servers
net maxrid          Display the maximum RID currently used
net idmap           IDmap functions
net status          Display server status
net usershare       Manage user-modifiable shares
net usersidlist     Display list of all users with SID
net conf            Manage Samba registry based configuration
net registry        Manage the Samba registry
net eventlog        Process Win32 *.evt eventlog files
net printing        Process tdb printer files
net serverid        Manage the serverid tdb
net notify          notifyd client code
net tdb             Show information from tdb records
net help            Print usage information

```

I don't understand many things about samba or Linux environment, but the error cause may be related to this?
```

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)

```

Thanks

---

### Post by SeijiSensei on 2019-07-20
Could be a permissions problem. Try adding
```
force user = seg_1
```
to the declaration for the Private share.

---

### Post by Morbius1 on 2019-07-20
> $ net online info --long
Invalid command: net online
You ran the wrong command. It's:
```
net usershare info --long
```

Is the Windows user on the Linux server a member of both the "users" group and the "windows_admin" group?

[COLOR=#0000cd]**EDIT**: Um ... Or are you actually trying to access each share with a different set of credentials?

If that is the case then Windows does not allow that sort of thing through explorer. What you can do is "map" the network "drive" then you are given the change to connect using a different username and password.
[/COLOR]

---

