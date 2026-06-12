---
title: "Samba Active Directory Windows 7 roaming profil"
date: 2019-01-10
forum: Server Platforms
---

### Post by argschlimm on 2019-01-10
Hi together,

first of all, I'm very new to the Samba world, so please excuse any misunderstandings.

My company has considered switching from a Windows Domain to an open source solution, which leads to me testing the feasibility of such a migration. Currently I'm checking out Zentyal which is Ubuntu based and runs with a Samba AD. I have achieved to set up the Zentyal as the DC and also include several  clients into the domain. When it comes to roaming profiles, the Windows 10  machines are working properly, first logon creates a corresponding  profile folder with the typical ".V6"-suffix. However, once a user logs  into the system using a Windows 7 client, no V2-profile folder is  created. Even when I provide a given V2-folder copied from an existing  user, the client still only works on a temporary profile.

The system is an Ubuntu 18.04 LTS and Samba 4. This is the smb.conf:

[global]
    workgroup = xxx
    realm = xxx.LOCAL
    netbios name = dc2019-1
    server string = Zentyal Server
    server role = dc
    server role check:inhibit = yes
    server services = -dns
    server signing = auto
    dsdb:schema update allowed = yes
    ldap server require strong auth = no
    drs:max object sync = 1200

    idmap_ldb:use rfc2307 = yes

    winbind enum users = yes
    winbind enum groups = yes
    template shell = /bin/bash
    template homedir = /home/%U

    rpc server dynamic port range = 49152-65535

    interfaces = lo,eth0
    bind interfaces only = yes

    map to guest = Bad User

    log level = 3
    log file = /var/log/samba/samba.log
    max log size = 100000



    include = /etc/samba/shares.conf



[profiles]
    path = /home/samba/profiles
    browseable = no
    read only = no

[netlogon]
    path = /var/lib/samba/sysvol/xxx.local/scripts
    browseable = no
    read only = yes

[sysvol]
    path = /var/lib/samba/sysvol
    read only = no



Any clues? Unfortunately I have not found anything that says it's a known problem..

---

