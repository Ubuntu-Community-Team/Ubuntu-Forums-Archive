---
title: "UFW Set Off"
date: 2012-11-01
forum: Security
---

### Post by fleamour on 2012-11-01
I just randomly tried:
```
sudo ufw status
```
It said it was not active, so I enabled via:
```
sudo ufw enable
```

I am now told; enabled on startup.  Should I be worried it was off? Does Xubuntu not auto enable during fresh install?

:confused: :( :confused:

---

### Post by Hungry Man on 2012-11-01
It's not on by default because you won't have any ports open by default except for dhclient and system services that you'd be allowing through anyways.

---

### Post by fleamour on 2012-11-01
OK, just read sticky.  Phew! Heart stopping moment!

---

