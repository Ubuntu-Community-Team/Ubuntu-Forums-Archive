---
title: "Setting up a working Samba PDC with standalone machines"
date: 2010-09-21
forum: Server Platforms
---

### Post by grajea01 on 2010-09-21
Hi,

I'm trying to set up a small LAN with a working Samba PDC and I'm running onto multiple issues. This might be a quite a long mail, I want to make sure everyone understands my issue...

Here's my setup : LAN is on 10.0.0.0/255.248.0.0 (CIDR : /13)

Basically, I have multiple boxes, but here only two physical boxes are of interest:
- oslo (kubuntu 10.04) on IP 10.2.1.1  .. The main fileserver
- helsinki (kubuntu 10.04) on IP 10.4.2.1 .. the main dev machine
- oslo2 (win7 x64 ultimate) on IP 10.2.1.101 .. vmware box on oslo
- helsinki2 (win7 x64 ultimate) on IP 10.4.2.101 .. vmware box on helsinki

The domain is named "Aproxya.NET" .

I want my PDC to run on oslo, and all VMs to connect onto the PDC.
Some other machines might or might not connect to the PDC. All machines have the same local accounts, ie same usernames, and same uids/gids, for linux boxes.

The problem I have is that I want my local users onto my fileserver (oslo) to still be able to connect on their local, linux account, while I want the same usernames to be able to use the PDC.

Variably, and I can't isolate when/why/who, pdbedit -Lv userONE would tell me that userONE has oslo for domain, some other time that is has aproxya.net, some other time, it has a hostname belonging on my LAN as domain name. I just can't figure that one out !

Last thing: I want some shares on the fileserver to be available for ALL my machines on my LAN, regardless of their status (authenticated throught the PDC or not).

Here's a snippet from my current smb.conf, if it might help.

```
[global]
        workgroup = APROXYA.NET
        server string = %h
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\s
successfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        logon script = logon.cmd
        logon drive = Z:
        domain logons = Yes
        os level = 33
        preferred master = Auto
        domain master = Yes
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0775
        directory mask = 0775
        browseable = No
        browsable = No

[netlogon]
        comment = Network Logon Service
        path = /srv/samba/netlogon
        guest ok = Yes

[profiles]
        comment = Users profiles
        path = /srv/samba/profiles
        create mask = 0600
        directory mask = 0700
        browseable = No
        browsable = No

[sharepoint]
        comment = share point
        path = /sharepoint
        read only = No
        create mask = 0775
        directory mask = 0775

```

(here, sharepoint is one of those shares that I want available to all my LAN).

I've created the required directories in /srv/samba/* . Funny thing, is that for one of my local users on oslo (the fileserver/PDC), a profile directory showed up into his $HOME, while nothing appeared in /var/samba/profiles/

All users have been added to SAMBA with smbpasswd -a USERNAME . All machines that should connect onto the PDC have been added to SAMBA with smbpasswd -a m MACHINE_NAME.

I just don't know what else I should try. Do you fine people have an idea ?

Thanks,

Jeff

---

