---
title: "Samba questions"
date: 2008-10-06
forum: Server Platforms
---

### Post by TheGameAh on 2008-10-06
I've tried researching it to death, and it seems like it might be possible, but I'm still not very clear.

Basically, the ultimate goal I'm trying to do is replace our Active Directory file server.  Not Active Directory itself, but I'd like to move the shares to a SAMBA server, that's integrated into Active Directory, so I can use existing AD users and groups.

Now I've seen all the info regarding integrating Samba into AD.  But what about permissions?  What if I wanted to have different sub folders with different permissions?  I've seen nothing on this.  Is it possible?

---

### Post by cdenley on 2008-10-06
> **TheGameAh said:**
> I've tried researching it to death, and it seems like it might be possible, but I'm still not very clear.

Basically, the ultimate goal I'm trying to do is replace our Active Directory file server.  Not Active Directory itself, but I'd like to move the shares to a SAMBA server, that's integrated into Active Directory, so I can use existing AD users and groups.

Now I've seen all the info regarding integrating Samba into AD.  But what about permissions?  What if I wanted to have different sub folders with different permissions?  I've seen nothing on this.  Is it possible?

It sounds like you want to use ACL's.
[https://help.ubuntu.com/community/SettingUpSamba#Installation](https://help.ubuntu.com/community/SettingUpSamba#Installation)

---

