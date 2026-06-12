---
title: "Samba share guest access issues"
date: 2016-04-25
forum: Server Platforms
---

### Post by wab2 on 2016-04-25
Hi all 

Having some unusual behaviour from samba server. With following config 

```
[global]
   workgroup = workgroup
   map to guest = bad user
   guest account = nobody
   encrypt passwords = true
   security = user


[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    guest ok = yes
    read only = no
    browseable = yes
    public = yes
    available = yes
    create mask = 0777
```


Essentially - this works for guest access from windows machines, but doesn't work on OSX. I can get access from OSX 10.11.4 but only when I log in with username + password. 

Has anybody had this issue or perhaps know of a solution? I know this isn't limited to my mac, as have tested it on others. 

Thanks.

---

### Post by wab2 on 2016-04-26
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572301](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572301)

---

### Post by Morbius1 on 2016-04-26
This isn't a solution to the underlying problem but what I did on my Linux box was the exact same thing I do on my Windows boxes:

I create a user named: smbuser
I give it the literal password of: smbuserpw
Then I add smbuser to the samba password database.

When my OSX clients access the Linux box they pass smbuser / smbuserpw.

*Probably should have made the user name smbguest but the precedent had been set so ...*

---

### Post by Morbius1 on 2016-05-04
The Ubuntu repositories now have the latest samba release - 4.3.9 - which fixes this issue. At least for me.

---

