---
title: "Samba Share in Docker Container"
date: 2016-03-08
forum: Virtualisation
---

### Post by motobeats on 2016-03-08
I setup a samba share in a KVM and it has been working great for over a year now. Only complexity is I have guest ok = no for some of the shares.

I have been trying to move the samba service into a ubuntu docker container. I can get it working as guest but connecting as a user has been flaky. With the latest settings I cannot navigate to the share ("The location is not a folder.") from my Mint desktop but can navigate directly to folders within the share. 

The sole share in smb.conf that I am trying to connect to (smb://ubuntu/backups)
```
[backups]
   comment = Backups
   path = /srv/samba/backup
   browsable = yes
   valid users = andrew 
   guest ok = no 
   read only = no
   create mask = 0755

```

Permissions on the share root
```
root@files:/srv/samba/backup# ll ..
total 12
drwxr-xr-x 3 root root 4096 Mar  6 02:10 ./
drwxr-xr-x 3 root root 4096 Mar  6 02:08 ../
drwxrwxrwx 5 root root 4096 Mar  8 22:43 backup/

```

Output of testparm
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[backups]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast, host, lmhosts, wins
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[backups]
    comment = Backups
    path = /srv/samba/backup
    valid users = andrew
    read only = No
    create mask = 0755

```

---

