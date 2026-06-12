---
title: "Change process owner"
date: 2007-09-05
forum: Server Platforms
---

### Post by Frunktz on 2007-09-05
Hi!
I have some script in init.d that going to launched in rc.2 but they run with root privileges.
Is there a way to change a process owned by root to be owned by another user.
Thanks

---

### Post by GigaVolt on 2007-09-05
Hello,

I have one little idea. Add "sudo -u USER" before you are program. This change owner for current process

---

### Post by Frunktz on 2007-09-05
It can works!
Now I try.
Thanks a lot.

---

