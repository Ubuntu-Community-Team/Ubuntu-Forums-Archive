---
title: "smb.conf permission issue"
date: 2009-08-11
forum: Server Platforms
---

### Post by reckless2k2 on 2009-08-11
I've got a directory share for scans used by every family member. I want to make it so that each user can't accidentally delete any persons scans they uploaded. 

Is it a create mask issue? I can't figure it out.

```
[scans]
     comment = Scan Directory
     path = /scans
     valid users = @scans
     writeable = yes
```
 
The share has group "scans" r/w permissions.

---

### Post by pizmooz on 2009-08-11
try adding
```
read only = no
```

---

### Post by reckless2k2 on 2009-08-12
To be clear, everyone can write now without a problem but can accidentally delete scans put in the directory by others. 

I'm trying to prevent them from being able to delete another persons scans. 

I already have writeable = yes so I'm not sure how ready only = no will help. 

I think it's a masking issue:

create mask
security mask

????

---

### Post by Iowan on 2009-08-12
Hopefully I'm mistaken, but "write access" would seem to suggest "delete access".

---

