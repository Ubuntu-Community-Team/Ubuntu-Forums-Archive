---
title: "SFTP Chroot question"
date: 2011-12-10
forum: Server Platforms
---

### Post by Rob_H on 2011-12-10
Hi. I'm trying to set up an SFTP server for a small workgroup with the following requirements:

[LIST=1]
[*]The SFTP users are chroot jailed to their home directories. They have no shell access.
[*]A special user group called "sftpadmins" should be able to read or write any file/directory of the SFTP users' directories. These admins do have shell access, but they're not root.
[/LIST]

I can set up the SFTP chroot configuration easily enough. But how do I set up the group permissions so that the non-root admins can read/write the directories? Do I have to make them world readable/writable?

---

