---
title: "Share Share Issues"
date: 2012-03-06
forum: Server Platforms
---

### Post by Muhnamana on 2012-03-06
Frustration with this issue is mounting and I'm fairly new when it comes  to Samba and Ubuntu in general but I have 2 users setup on my Ubuntu  box, user1 and user2. These same two users are added within Samba as  well.

user1 is currently logged in on the machine and has an external hdd mounted.

I have a current share setup within Samba as the following:

```
[music]
comment = Music
browseable = yes
path = /media/MyPassport2
read only = no
public = yes
guest = yes
create mask = 0777
directory mask = 0777
```When connecting to this share from Windows 7, user1 can connect fine. user2 cannot access this share.

If I throw in the ```
force user = user1
```, then user2 can connect.

Does this have something to do with user1 having the drive mounted? Permissions issue possibly?

Any and all suggestions are welcome. As I said, I'm pretty much stuck.

Thanks!

---

### Post by nsnidanko on 2012-03-09
Seems like a permission problem. I would check owner and group of the /media/MyPassport2 directory. Also check chmod.
Try mounting drive under root and see if user1 fails to access as well.

---

### Post by Morbius1 on 2012-03-09
>  Does this have something to do with user1 having the drive mounted? Permissions issue possibly?Yes.

If the MyPassport2 is inserted or turned on when user1 is logged in and the partition is formatted to NTFS or FAT32 then it will automatically mount with user1 as owner and permissions to read or write permitted only to user1. "force user" is a legitimate way in Samba to deal with this particular issue.

---

