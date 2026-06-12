---
title: "SSH, Chrooting and user groups"
date: 2009-01-10
forum: Server Platforms
---

### Post by charlesvallieres on 2009-01-10
Hi,
I'm setting up a web server and so far, everything was easy and simple.
Now I've set sftp (with openssh) and I'd like to have 2 groups of people, sftp-users and sftp-admins, both groups are setted and chrooted correctly, now my question is : How can I set the group sftp-admins to have complete access over the directories of sftp-users? I've searched and everything I tried didn't work.
Thanks!

---

### Post by RealPSL on 2009-01-11
I would recommend 2 things first make sure that the umask of the users uploading the files is 007 or anything else that gives group write access. You can then make the directories that are being uploaded setgid so the group of the files is always the same as the parent directory. You can then add the sftp-admin users to the sftp-users group so they can overwrite the files since they will have write permissions

---

