---
title: "system policy prevents....."
date: 2010-07-19
forum: Security
---

### Post by kainalu on 2010-07-19
Hello all,

I have this message that tells me that system policy prevents shutting down when other users are logged in. I want to remove this policy. Where can system policies be changed?

THANKS!

---

### Post by sisco311 on 2010-07-19
Create a new policykit rule to allow admin users to shutdown and restart when other users are logged in. Create a new file:
```
gksu gedit /var/lib/polkit-1/localauthority/50-local.d/shutdown-restart.pkla
```

with the following content:
```

[system shutdown/restart]
Identity=unix-group:admin
Action=org.freedesktop.consolekit.system.stop-multiple-users;org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes
```

save it and exit.

---

### Post by kainalu on 2010-07-19
Thanks!

---

### Post by sisco311 on 2010-07-19
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

