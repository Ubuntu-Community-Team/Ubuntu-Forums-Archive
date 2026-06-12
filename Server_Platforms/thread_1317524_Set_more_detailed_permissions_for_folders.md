---
title: "Set more detailed permissions for folders"
date: 2009-11-06
forum: Server Platforms
---

### Post by wesg on 2009-11-06
I've set up my server for file transfer to Macs and PCs, and have set the permissions to what I want. As the owner I can change files, but the group can only read. This works more of less, but I have a few users that I want to be able to write to the directory.

How can I specify users from the group that have different permissions?

---

### Post by Thirtysixway on 2009-11-06
Just a shot in the dark here...

If you have a group for only users you want to have read-only access, you could do folder permissions like

757

The owner can read,write,execute  group can read, others can read,write,execute.  I could be wrong on this, I'd try it out though.

---

### Post by sisco311 on 2009-11-06
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

acl

---

