---
title: "Samba Hosts Allow Option"
date: 2006-03-13
forum: Server Platforms
---

### Post by emut on 2006-03-13
Have Samba setup on a server install of Breezy for a small business.  Everything works fine apart from trying to limit access to one of the shared folders through Samba for some Windows ME and XP Home boxes.

The /etc/samba/smb.conf

```
#======================= Global Settings =======================

[global]
workgroup = shop

#======================== Authentication =======================

security = user

#======================= Share Definitions =====================

[abc_shared]
path = /home/abc/abc_shared
writable = yes
force user = abc
force group = abc
create mask = 777
directory mask = 777
hosts allow = 192.168.1. localhost

[dir_shared]
path = /home/directors/directors_shared
writable = yes
force user = directors
force group = directors
create mask = 771
directory mask = 771
hosts allow = 192.168.1. localhost
hosts deny = 192.168.1.2 192.168.1.3 192.168.1.4

```

And a testparm

```
colin@server:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[abc_shared]"
Processing section "[dir_shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = SHOP

[abc_shared]
        path = /home/abc/abc_shared
        force user = abc
        force group = abc
        read only = No
        create mask = 0777
        directory mask = 0777
        hosts allow = 192.168.1., localhost

[dir_shared]
        path = /home/directors/directors_shared
        force user = directors
        force group = directors
        read only = No
        create mask = 0771
        directory mask = 0771
        hosts allow = 192.168.1., localhost
        hosts deny = 192.168.1.2, 192.168.1.3, 192.168.1.4
colin@server:~$

```

What I am trying to achive is having everyone being able to read-write to the abc_shared folder and only the directors being able to access the dir_shared folder.

At present everyone all the Windows clients access both shares.  Each of the directors has a user account on the server added into a group called directors, the other PC's access the abc_shared forder with the username abc which is created on the server.

I really am stuck as how to deny access to the PC's that shouldn't be able to access the dir_shared folder?

Any ideas?

---

### Post by emut on 2006-03-13
Success!

I got it working by using valid users = Username 1 Username 2 etc, and by adding

```
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd

```

---

### Post by Iowan on 2006-03-13
Another option is to build a group (called directors?) and make **valid users = @directors**.  You'd then add desired users to the directors group.

---

### Post by emut on 2006-03-13
Thats a better solution, then a new user can just be added to the group rather than having to change the smb.conf, thanks :)

---

