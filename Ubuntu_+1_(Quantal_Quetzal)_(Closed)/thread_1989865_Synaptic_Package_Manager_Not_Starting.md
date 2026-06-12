---
title: "Synaptic Package Manager Not Starting"
date: 2012-05-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by williejones on 2012-05-28
Synaptic is not starting from the side bar.  It runs fine with terminal sudo-synaptic.  Anyone else seeing this?

---

### Post by Yellow Pasque on 2012-05-28
It works fine for me (but I run xfce/xubuntu). BTW, you should use gksu instead of sudo for graphical applications:
```
gksu synaptic
```

---

### Post by mc4man on 2012-05-28
synaptic was failing to start here for a few days, atm  seems to have cleared up 

The reason for it not starting would be the auth window not opening, forget the error.

When that's happening from the icon you could run the command now being used & that should also fail with the error

current command used
```
synaptic-pkexec
```

---

### Post by williejones on 2012-05-29
> **Temüjin said:**
> It works fine for me (but I run xfce/xubuntu). BTW, you should use gksu instead of sudo for graphical applications:
```
gksu synaptic
```

Thanks for the reminder to use gksu. Synaptic is starting from the side panel today.

---

