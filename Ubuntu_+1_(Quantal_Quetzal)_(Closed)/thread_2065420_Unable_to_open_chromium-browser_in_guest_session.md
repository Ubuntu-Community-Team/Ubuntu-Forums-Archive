---
title: "Unable to open chromium-browser in guest session"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-01
when i try to run it i get this 
```
Failed to move to new PID namespace: Operation not permitted
```
not a big deal i just use firefox

---

### Post by mc4man on 2012-10-01
just saw a changelog mentioning this

> lightdm (1.3.3-0ubuntu5) quantal; urgency=low

  * debian/patches/08_lp1059510.patch: allow owner 'rw' access to
    /{,var/}run/user/guest-*/dconf/user. Also allow owner writes to sockets in
    /{,var/}run/user/guest-*/keyring-*/. (LP: #1059510)
  * debian/patches/09_lp577919-fix-chromium-launch.patch: allow launch of
    chromium-browser from guest session. (LP: #577919)

 -- Jamie Strandboge <jamie@ubuntu.com>  Mon, 01 Oct 2012 10:15:51 -0500

---

### Post by pqwoerituytrueiwoq on 2012-10-01
ok guess it will be fixed next time i boot my laptop in that case
i have no idea why i am liking this install so much more than the old mint 13 xfce install i had

---

