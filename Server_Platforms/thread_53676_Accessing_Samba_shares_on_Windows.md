---
title: "Accessing Samba shares on Windows"
date: 2005-08-01
forum: Server Platforms
---

### Post by Sundel0802 on 2005-08-01
Ok, I've got shares set up on both Windows and Ubuntu. From Ubuntu, I can read and write to shares on Windows with no problem. From Windows however, when I attempt to access my Ubuntu shares I get prompted for a username and password. I havn't set one up (that I know of) and anything I try to enter is rejected. Curiously, I can access Ubuntu shares from XBMC on my Xbox (for those of you familiar with it) with no problem.

So, how do I access Ubuntu shares from Windows, and better yet, be able to do it without being prompted for a password.

---

### Post by drummer on 2005-08-01
[http://ubuntuforums.org/showthread.php?t=53096](http://ubuntuforums.org/showthread.php?t=53096)

not sure about without a password.. must be possible though

---

### Post by Sundel0802 on 2005-08-01
Ok, so I've almost answered my own question. In /etc/samba/smb.conf, I changed

```
; security = user
``` to ```
security = share
``` 

This lets me browse and read from the share without any sort of user/pass prompt but I can't write to it. I'd still like to figure out how to be able to write to the share without a user/pass prompt but this will suffice for now.

---

### Post by LordHunter317 on 2005-08-02
Ick.  No.  I wish Ubuntu would just disable security share.  It's deprecated security tech.

What you need to do is create a Samba password for you user account.  Run:```
sudo smbpasswd -a myusername
```And type in a password.  Then connect to your Ubuntu box using your username and that password.

---

