---
title: "default group permissions"
date: 2006-02-03
forum: Server Platforms
---

### Post by afonit on 2006-02-03
hello, how do you set the default group permissions, so that every time you create a file it will inherit the desired defaults?


for example - my situation:

at work, we have an os x 10.3.9 server
I use ubuntu breezy.

access the server through smb with a login, that my login name belongs to the group 'production'

when I create files locally they have permissions of read write execute by me, but for group they are missing the permission of write.

how do I get the defaults for all files to be writeable by the group permissions?

---

### Post by afonit on 2006-02-03
is that a preset that I should be able to set on my local computer, or is that a present that would be on the server computer?

---

### Post by lol on 2006-02-03
If you only want to change the permissions for files created via samba, that can probably be done with a small change in the configuration file:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2581668](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2581668)

If you want a better way to manage files permissions created both via samba and from the host computer, you may consider using Access List Control (ACL). The thing is, samba needs to be compiled with support for this, and I don't know it is the case on Ubuntu.

---

### Post by LordHunter317 on 2006-02-03
What permissions a file has is controled by the 'umask'.  'umask' defines the bits that are **removed** from newly created files/directories.

If you're using a shell, set your umask to '007' or similar before creating files you want group write access on.

To change the ownership by default however, you need to place the 'setgid' bit on the directory, which will cause all newly created files on the directory to have the directory's group ownership.


However, whenever I look at changing my default umask, I usually set an ACL and forget about it.

---

### Post by afonit on 2006-02-03
thank you for the ideas, I will research those.


again,


much appreciated.

---

