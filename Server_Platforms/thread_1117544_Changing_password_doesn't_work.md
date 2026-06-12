---
title: "Changing password doesn't work"
date: 2009-04-06
forum: Server Platforms
---

### Post by tr333 on 2009-04-06
When I attempt to change the password for the logged-in user, it doesn't ask me for a new password.  It asks me for my current password and then exits:
```

ubuntu@ubuntu:~$ passwd
Changing password for ubuntu.
(current) UNIX password:
passwd: password updated successfully
ubuntu@ubuntu:~$

```

---

### Post by _Purple_ on 2009-04-06
Are you using likewise-open by any chance? If you are, then this [link](http://ubuntuforums.org/showthread.php?t=1072851.html) might solve your problem.

---

### Post by tr333 on 2009-04-06
Thanks.  That looks like it might be the problem.  I'll try installing libpam-cracklib tomorrow.

---

### Post by zeki893 on 2009-04-10
try this first
```
apt-get remove likewise
```

---

