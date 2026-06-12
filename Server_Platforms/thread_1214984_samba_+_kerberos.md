---
title: "samba + kerberos"
date: 2009-07-16
forum: Server Platforms
---

### Post by Belnoctourne on 2009-07-16
im having very wierd issues with my samba behavior running on my server, its joined to my ad domain but failing to authenticate samba sessions, I can log into ssh with domain accounts for example the account belnoctourne exists only on the domain and ssh works perfectly and I can browse and read all of the files shared by samba correctly however when I attempt to connect the same account through samba everything goes to hell, everything seems to be joined correctly and im running all the diagnostic commands I can think of to try and find why this isnt working, any help would be very appreciated

in the network things work as follow

the linux box (blackbeard) runs dhcp secondary dns and nat
the windows box (davyjoneslocker) runs the domain and dns
name resolution works fine from any host in the network even for local hosts the users on the domain are all a member of the windows security group shares

wbinfo -K --krb5auth=YARRRG\\belnoctourne%password
```

plaintext kerberos password authentication for [--krb5auth=YARRRG\belnoctourne%password] succeeded (requesting cctype: FILE)
credentials were put in: FILE:/tmp/krb5cc_0

```

wbinfo -g
```

domain computers
domain controllers
schema admins
enterprise admins
cert publishers
domain admins
domain users
domain guests
group policy creator owners
ras and ias servers
allowed rodc password replication group
denied rodc password replication group
read-only domain controllers
enterprise read-only domain controllers
dnsadmins
dnsupdateproxy
**shares**
dhcp users
dhcp administrators
ubuntuadmins

```

wbinfo -u
```

BLACKBEARD\nobody
...
...
**belnoctourne**
...
...

```

net ads info
```

LDAP server: 10.0.0.200
LDAP server name: davyjoneslocker.yarrrg.net
Realm: YARRRG.NET
Bind Path: dc=YARRRG,dc=NET
LDAP port: 389
Server time: Thu, 16 Jul 2009 15:56:35 EDT
KDC server: 10.0.0.200
Server time offset: 376

```

/etc/samba/smb.conf
```

[global]
        log file = /var/log/samba/%m
        idmap gid = 600-20000
        winbind trusted domains only = yes
        encrypt passwords = yes
        winbind use default domain = Yes
        realm = YARRRG.NET
        template shell = /bin/bash
        wins support = true
        server string = Blackbeard
        printing = cups
        idmap uid = 600-20000
        winbind nested groups = Yes
        workgroup = YARRRG
        os level = 20
        printcap name = cups
        security = ads
        preferred master = no
        max log size = 50
        log level = 3
#        winbind separator = +

[animation]
   writable = no
   create mode = 755
   path = /media/CNPM/animation
   directory mode = 755
   valid users = @shares

[audio-books]
   writable = no
   create mode = 755
   path = /media/CNPM/audio-books
   directory mode = 755
   valid users = @shares

[emulators]
   writable = no
   create mode = 755
   path = /media/CNPM/emulators
   directory mode = 755
   valid users = @shares

...more random shares...

[upload]
   writeable = yes
   create mode = 775
   path = /media/CNPM/upload
   directory mode = 775
   valid users = @shares

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
   valid users = @shares

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   valid users = @shares


```

---

