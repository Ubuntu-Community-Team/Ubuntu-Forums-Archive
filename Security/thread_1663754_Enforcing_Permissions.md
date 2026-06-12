---
title: "Enforcing Permissions"
date: 2011-01-10
forum: Security
---

### Post by gerowen on 2011-01-10
I have a shared external hard drive on my local network.  Here's kind of a breakdown of permissions.

Two users, "marcus" and "ash".
Both users are members of the group "adams".
Owner of the external (/media/Storage) is "marcus".
Group of the external (/media/Storage) is "adams".
Applied the following command for permissions:
sudo chmod -R 770 /media/Storage

However if I browse the folder using the smb share and make changes, my wife who is logged onto her account locally on the desktop cannot modify my folders or files until I reapply the permissions.  If I make changes using my account locally it's not an issue, only when browsing with my account over samba.  Is there a way to fix this?

---

### Post by mikewhatever on 2011-01-10
Try changing the creating mask in /etc/samba/smb.conf.

> # File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


---

### Post by Morbius1 on 2011-01-10
In addition to the "create mask" suggested by mikewhatever I'm fairly certain you will need to add a "force group":
```
force group = adams
```Otherwise when remote marcus creates a file it will save as:

owner:group = marcus:marcus
permissions = 664

It's not going to do ash any good unless ash is a member of the marcus group.

With a "force group" it will save as maucus:adams

---

