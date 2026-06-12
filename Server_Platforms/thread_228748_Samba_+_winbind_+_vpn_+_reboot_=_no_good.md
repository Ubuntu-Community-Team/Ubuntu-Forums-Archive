---
title: "Samba + winbind + vpn + reboot = no good"
date: 2006-08-03
forum: Server Platforms
---

### Post by jakedh on 2006-08-03
I've been working on creating a domain controller which serves a couple of computers for single-login, sharing, and VPN with winbind. I have samba working for the domain part and the VPN function works too, but...
Before I can use a VPN I must first join my own domain????!!!!
```

net join -U root
```
...so I do this and all is grand but if I reboot I have to rejoin before VPNs will work again. This is not an acceptable solution. It needs to be automatic and the very fact that it does this leads me to believe there is some other problem.

Does anyone have a clue what I might be doing wrong? I have scoured the internet and have become more than frustrated to find my same question unanswered, from 1999...](*,) 

Some usefull info:

```


Load smb config files from /etc/samba/smb.conf
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[backup]"
Processing section "[team]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_DOMAIN_BDC
Press enter to see a dump of your service definitions

[global]
        workgroup = FSAE
        realm = FSAE
        security = USER
        obey pam restrictions = Yes
        password server = xxxxxx
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spas sword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        client NTLMv2 auth = Yes
        client lanman auth = No
        client plaintext auth = No
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        logon script = logon.cmd
        logon path = \\%N\profiles\%U\winprofile
        logon drive = U:
        logon home = \\puma\%U
        domain logons = Yes
        domain master = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind use default domain = Yes

[netlogon]
        path = /var/lib/samba/netlogon

[profiles]
        path = /home
        read only = No
        create mask = 0600
        directory mask = 0700

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[backup]
        path = /backup
        guest ok = Yes

[team]
        comment = 2007
        path = /team
        read only = No
        guest ok = Yes

```

---

