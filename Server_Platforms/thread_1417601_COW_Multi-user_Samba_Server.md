---
title: "COW Multi-user Samba Server"
date: 2010-02-27
forum: Server Platforms
---

### Post by coolsvilleman on 2010-02-27
Hi All,

I have a very specific problem regarding Copy-On-Write in a multi-user samba server environment under Ubuntu Server edition. I have my samba server setup and sharing files normally but I want to do adapt the setup so I can have the following situation:

The Samaba server shares files as normal. Windows users can login and read any file or directory their account has permissions to read. When a user tries to write to a file or directory however I would like it to make a new copy of the file/directory in the users home directory and then write the changes to the new file/directory. Any other users who uses the samba share would see the original file or their own version of the file if they previously modified it.

This must be a solved problem and has a ton of potential applications for application/file streaming. I searched around but couldn't find anything similar to this type of scenario? Free/open-source solutions would be the best of course.

Any suggestions would be very much appreciated.

---

