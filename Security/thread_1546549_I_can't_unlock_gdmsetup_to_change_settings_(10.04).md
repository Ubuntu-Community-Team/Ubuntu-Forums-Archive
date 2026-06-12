---
title: "I can't unlock gdmsetup to change settings (10.04)"
date: 2010-08-05
forum: Security
---

### Post by alex04210 on 2010-08-05
when lauching gdmsetup I can't unlock it to change settings. nothing happens when clicking on "lock" button:(

the same problem in Ubuntu Software Center 2.0.7. nothing happens when I pull "Install"
(no authorization starts)

there are no  authorization window in admin-shares too

It started when I have changed the type of ubuntu login - I have changed from gdmsetup settings from "password" to automatic authorization.

I checked the the PolicyKit  Agent. It seems to working (and autostarting) with such command:
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
so it's ok

can someone help me?

---

### Post by Dezertflower on 2010-08-30
I solved this problem by temporarily allowing root to log in to the desktop.  Then as root running the gdmsetup utility.  It will unlock as the user is root. The settings can then be changed.

Afterward, I took out the ability for root to log in.

---

### Post by cariboo on 2010-08-30
If you start gdmsetup as a normal user, you should be able to unlock it. I just tried it using:

```
gksu gdmsetup
```

and it wouldn't unlock for me.

---

