---
title: "Samba Share: Hide shared folders from unauthorized users"
date: 2009-12-02
forum: Server Platforms
---

### Post by Meelad on 2009-12-02
**System:** Ubuntu 9.10.

I installed samba and shared a few folders on the local network. It works fine apart from this problem..

**Problem:** I can't hide shared folders from a selected group of users while show them to another group, like the way it is in [homes] sharing, where if I log in as user1 (with the [homes] sharing set up in smb.conf) I can only see user1 home folder. While when user2 logs in he'll see user2 home folder and none of the other members' home folders. I want to do the same thing but with custom folders. At the moment I can specify which users have access to the folder (so a selected group of users will have their access denied to that directory), but I thought it will be more convenient if they don't get to see the folder in the first place if they don't have any rights for it.

**Already tried:**
- Sharing the folder through ubuntu (right click on the folder => share...) and set exclusive rights for the owner, while group and other members' rights were set to (none).
- Sharing the folder through smb.conf. I set the masks (create and directory) to 0700, and already set the valid users exclusively to the owner of the folder.

In both occasions exclusive access to the folder by the owner works perfect, but everybody can still see the folder (though can't get in). How can I hide it from them?

Any help is very much appreciated.

---

### Post by koenn on 2009-12-02
```
[TheShare]
   ...
   hide unreadable = yes
```
will only show files/folders in TheShare if the user has read access to them. So no access = invisible.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by Meelad on 2009-12-04
It worked like a charm!!

Thanks A TON!!  :guitar:

=D>=D>=D>=D>=D>

---

