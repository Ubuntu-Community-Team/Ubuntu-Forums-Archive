---
title: "Guest login help"
date: 2009-08-18
forum: Server Platforms
---

### Post by stretch427 on 2009-08-18
I want to create accounts for my friends to log on to my server with, and I'm having trouble. I've used adduser and gone through all the password making and stuff, but when I log out and test it, it says access denied. I'm sure it's a really easy fix i'm just not quite sure what to do. Thanks!

---

### Post by kangyu29 on 2009-08-19
did you use "users and groups" program under "administration"?
that should take care it.

---

### Post by stretch427 on 2009-08-19
I actually figured it out, I had blocked my 
```
 AllowUsers <username> 
```
in my /etc/ssh/sshd_config file. Simply uncommented them and it works now! 
Thanks for the help anyway! Cheers!

---

