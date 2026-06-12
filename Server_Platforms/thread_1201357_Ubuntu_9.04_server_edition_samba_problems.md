---
title: "Ubuntu 9.04 server edition samba problems"
date: 2009-07-01
forum: Server Platforms
---

### Post by Msingh on 2009-07-01
I want to make my folder and my brothers' folders invisible and have a public folder accessible to all. If i'm not clear enough, I want each user only able to see their own folder, and the public folder, and guests only allowed to see the public folder.

here is an example of one of the folders in my samba.conf.master file:

[*username*]
    comment = *username*'s server
    path = /home/*username*
    browsable = yes
    guest ok = no
    read only = no
    writeable = yes
    valid users = *username*
    write list = *username*
    create mask = 0755

I tried making them not browsable, but then the user couldn't see his own folder.... please help!

---

### Post by Avinash.Rao on 2009-07-01
Msingh,

The share name is the brackets should be [home] which simply means the home directory, and not username. When the [home] share is mentioned any user logging into the samba domain will have their respective home directories mapped as a network drive. And, the home directory should be in /home/username

Hope this helps.

---

### Post by swerdna on 2009-07-01
For the public share:
```
[share_name]
path = /path_to/shared_directory
read only = no
force user = a_user
guest ok = yes
```
Chown the shared directory to ownership a_user:a_user and chmod the directory to 755 with:
```
chmod 755 /path_to/shared_directory
chown -R a_user:a_user /path_to/shared_directory
```

For the private shares:
```
[homes]
comment = Home Directories
valid users = %S
browseable = No
read only = No
inherit acls = Yes
```

This share allows access with full read/write permissions to users logged onto either Windows or Linux clients on the LAN. You need to supply your Linux username and Samba password to access the share. It's called "roaming" because you can roam around the LAN and access your home on the server from all computers.

In Windows you can sometimes see the share as an icon named for your Linux username. Whether you see the icon depends on your transaction history with the server earlier that session. If you can see it, drill down into the share. If you can't see it then use an address like this in the Windows network browser: \\server_name\linux_username. Users logged onto other computers with usernames different from the Linux owners of the shares can't see the shares.

---

### Post by Avinash.Rao on 2009-07-01
Bingo!

---

### Post by swerdna on 2009-07-02
> **Avinash.Rao said:**
> Bingo!

My Grandmother gets a prize when she hears that. What about us........?

---

### Post by Avinash.Rao on 2009-07-02
:guitar::lolflag: 

I meant to say that the explanation was good and correct.

---

