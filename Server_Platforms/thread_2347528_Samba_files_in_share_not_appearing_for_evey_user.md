---
title: "Samba files in share not appearing for evey user"
date: 2016-12-26
forum: Server Platforms
---

### Post by tmartin99 on 2016-12-26
Running Ubuntu server 16.04 with Samba 4.3.11.  Workstations are a mix of PCs and Macs.

We have a strange issue with our newest file server.  Everyone has access to the same public share for basic files.  This share is completely open with anonymous, guest access so anyone can read, write or modify the files in it.  However some users are unable to view all of the files or folders in the shares. *User A *might create a new file in the share but *User B* is unable to see it.  Sometimes a folder or file that was previous visible to *User A* disappears from his share after *User B *opens or modifies it.  I'm relatively new to Samba so I am wondering if I made a mistake with the permissions or if there is another issue going on.

Thanks-you

Shared directory Permissions
```
drwxrwsrwx 78 nobody nogroup 12288 Dec 22 13:29 share 
```

share settings in smb.conf

```
[server]
browseable = yes
path = /mnt/data/share
guest ok = yes
read only = no
writeable = yes
create mask = 0777
directory mask = 0777



```

---

### Post by Morbius1 on 2016-12-26
> drwxrwsrwx 78 nobody nogroup 12288 Dec 22 13:29 share
You're part way there. You set the sgid bit so that newly added files and folders inherit the "nogroup" group if those files are added locally on the server.

Now you have to make the samba share definition do the same thing:

> [server]
browseable = yes
path = /mnt/data/share
guest ok = yes
read only = no
writeable = yes
[COLOR=#0000cd][B]force group = nogroup
create mask = 0664
force directory mode = 2775
[/B][/COLOR]
An alternate way is to simply force every client to this share appear to be the "nobody" user:
> [server]
browseable = yes
path = /mnt/data/share
guest ok = yes
read only = no
writeable = yes
[COLOR=#0000cd]**force user = nobody**[/COLOR]
It depends on how you use this server and what owner or process is adding files to the folder being shared locally.

---

