---
title: "Suspend option is disabled"
date: 2013-06-15
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-06-15
[IMG]http://i.imgur.com/ytOiNOQ.png?1[/IMG]
Screenshots:
[http://imgur.com/a/aygK2](http://imgur.com/a/aygK2)
Issues:
Suspend is disabled in menu
No suspend in logout dialog - [http://imgur.com/gKRp46M](http://imgur.com/gKRp46M)
password on restart
missing options for power/suspend/hibernate button pressed
edit:
i can use suspend from the lightdm login window, looks like a permission issue

---

### Post by pqwoerituytrueiwoq on 2013-06-20
Am i the only one with this issue?

---

### Post by neruson on 2013-06-21
Is xfce4-power-manager installed?

---

### Post by Elfy on 2013-06-21
While I do have the suspend button I would suspect it is all part of the password on logout/shutdown/restart issue - though I could be wrong.

[https://bugs.launchpad.net/xfwm4/+bug/1178373](https://bugs.launchpad.net/xfwm4/+bug/1178373)

---

### Post by pqwoerituytrueiwoq on 2013-06-21
> **neruson said:**
> Is xfce4-power-manager installed?yes

---

### Post by pqwoerituytrueiwoq on 2013-06-21
> **Elfy said:**
> While I do have the suspend button I would suspect it is all part of the password on logout/shutdown/restart issue - though I could be wrong.

[https://bugs.launchpad.net/xfwm4/+bug/1178373](https://bugs.launchpad.net/xfwm4/+bug/1178373)iirc that did not affect the guest account, this does

---

