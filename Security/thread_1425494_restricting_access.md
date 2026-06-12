---
title: "restricting access"
date: 2010-03-09
forum: Security
---

### Post by Irti on 2010-03-09
Hi... i wanted to restrict access in ubuntu for general users...for example.....users shouldn't be allowed to use menus at all....the system should log in automatically.....connect to a remote desktop connection on startup...users should not be able to use anything on the pc except for maybe the internet...How do i enable this configuration???

---

### Post by bodhi.zazen on 2010-03-09
Are you wanting to run a kiosk of some kind ?

If so, take a look at the kiosk functions.

Otherwise you can use apparmor. I lock down the guest account with apparmor (jailbash).

---

