---
title: "Protecting Samba Shares"
date: 2007-07-13
forum: Server Platforms
---

### Post by jcounsel on 2007-07-13
Because of unix permissions, I don't think there is an easy way ... but...:lolflag:

I am trying to keep windows users (XP Pro and Home) from being able to delete files on the Samba Share (fiesty).  I don't even know if the immutable modifier is available on fiesty or if it is implemented correctly.

So, is there an easier way than using the immutable modifier to prevent windows users from deleting files and folders on the samba share while allowing them the ability to create new and modify existing files?

Thanks...

---

### Post by Mr. C. on 2007-07-13
[ edit - sorry, misread ]

Any attributes you set in the linux file system will govern remote access as well.

Creating new files requires the ability to write to the directory, thus the directory must be writable by a user; this also implies that the same user can delete an the file from the directory.

Allowing file modification while trying to prevent file deletion seems challenging - what prevents a user from deleting the contents of the entire file, essentially rendering it useless?

What real world problem are you trying to solve ?

MrC

---

### Post by pgjensen on 2008-04-07
any way to do this?  real-world example for me is XP machines access the shares and I'd hate to get a virus on XP that deletes files from network shares!

---

