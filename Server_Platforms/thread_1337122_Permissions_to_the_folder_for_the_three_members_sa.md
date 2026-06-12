---
title: "Permissions to the folder for the three members samba"
date: 2009-11-25
forum: Server Platforms
---

### Post by redelek on 2009-11-25
Hi,
I have a little problem with the granting of permissions for three users in samba.
That is my shared participation
```
[ksiegowosc]
        path=/home/samba/ksiegowosc
        valid users = predel, ksiegowosc
        admin users = predel
        read only = No
        browseable = Yes
[OPERATING]
        path=/home/samba/ksiegowosc/OPERATING
        valid users = ksiegowosc, opf, opr
        admin users = predel
        read only = No
        write list = opf
        read list = opr
        browseable = Yes
        nt acl support = Yes
```Have even ran the ACL, but they do not have the effect.
If the user "ksiegowosc" will do a new file that you "opf" not for him to save. 
This happens, and vice versa. If the user "opf" file adds a new user "ksiegowosc" can not save the church.
What's most interesting work removal in all cases?
Can you help?

Best regards 
Redelek

---

