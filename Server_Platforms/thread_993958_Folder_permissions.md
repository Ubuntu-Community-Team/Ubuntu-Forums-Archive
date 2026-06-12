---
title: "Folder permissions"
date: 2008-11-26
forum: Server Platforms
---

### Post by jchristiansen70 on 2008-11-26
I have done some searching for this and not found it.  I am trying to create a home folder template, which I have done and works fine, except that I have one folder I want to have R/W.  This is a place for a group to share.  The folder works fine, but as expected, when a user places a doc in that folder the permissions are set to that user and the owner, and no one else as having R/W.  I can go in and change them, but is there a way to have all docs placed in the folder auto set to R/W for everyone?

Thanks

---

### Post by andrew.mckevitt on 2008-11-26
> **jchristiansen70 said:**
> I have done some searching for this and not found it.  I am trying to create a home folder template, which I have done and works fine, except that I have one folder I want to have R/W.  This is a place for a group to share.  The folder works fine, but as expected, when a user places a doc in that folder the permissions are set to that user and the owner, and no one else as having R/W.  I can go in and change them, but is there a way to have all docs placed in the folder auto set to R/W for everyone?

Thanks

I had the same problem setting up my home server, it's samba's default setting that need changing, I found this samba tutorial excellent and easy to follow. Since following it, I've managed to set up three private user folders, one public media folder - read only and a public folder with read/write for everyone. 

Here's the link, I hope it helps.

[http://www.samba.netfirms.com/index.htm](http://www.samba.netfirms.com/index.htm)

---

