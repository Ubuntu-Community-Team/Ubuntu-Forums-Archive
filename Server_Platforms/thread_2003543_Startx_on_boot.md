---
title: "Startx on boot"
date: 2012-06-14
forum: Server Platforms
---

### Post by xd1936 on 2012-06-14
Hello!

I'm currently making a super-slim thin client OS out of the Ubuntu Minimal image. I have everything perfect now; user logs in automatically, script runs with Openbox, etc.

All I need now is to have startx run on boot. Placing it in rc.local didn't work, it gave a "user is not allowed to do this" error.

What is the easiest way to have 'startx' run on login?

---

### Post by wojox on 2012-06-14
Install a Display Manager would be easiest.

There is also [Start X at Boot]("https://wiki.archlinux.org/index.php/Start_X_at_Boot").

---

### Post by xd1936 on 2012-06-14
Thank you for that link, it's just what I was looking for.

---

