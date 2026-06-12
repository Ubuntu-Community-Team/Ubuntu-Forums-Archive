---
title: "Ubuntu 10.4 Lost samba shares after SSL update."
date: 2012-05-26
forum: Server Platforms
---

### Post by eino1953 on 2012-05-26
Seems that the latest secure socket layer update, has lost my shares  with the other computers in my network. I would like to know how to fix  this problem.

---

### Post by eino1953 on 2012-05-27
I was not sure were to post this, So I chose the most obvious places. Sorry for the cross post.

---

### Post by eino1953 on 2012-05-27
I can connect with the other computers, going to connect to server. Then Windows server, and typing the computer names. On 3 different computers one running, Windows XP , the others is running Ubuntu 10.4 Both computers running 10.4 have the problem. The computer running Windows XP have no problem connecting to Both Ubuntu computers.

---

### Post by eino1953 on 2012-05-27
This is the testparm of the role domain member. I use this for storing backups, music, and movie files. ETC.
> koria@koria-desktop:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Processing section "[Videos]"
Processing section "[Music]"
Processing section "[Backups]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
    workgroup = KORIA
    server string = %h server (Samba, Ubuntu)
    security = DOMAIN
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = koria
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts host wins bcast
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Pictures]
    path = /home/koria/Pictures
    read only = No

[Videos]
    path = /home/koria/Videos
    read only = No

[Music]
    path = /home/koria/Music
    read only = No

[Backups]
    path = /media/mine
    read only = No
koria@koria-desktop:~$ 


---

### Post by CharlesA on 2012-05-27
Run this from one of the machines you cannot connect from:

```
smbtree
```

---

### Post by eino1953 on 2012-05-27
Nothing happens.
> koria@koria-desktop:~$ smbtree
Enter koria's password: 
koria@koria-desktop:~$ 


---

### Post by eino1953 on 2012-05-27
Thank you !! I got everything back after a restart.

---

