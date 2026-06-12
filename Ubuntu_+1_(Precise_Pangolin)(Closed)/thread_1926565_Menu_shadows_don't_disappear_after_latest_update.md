---
title: "Menu shadows don't disappear after latest update"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kyleabaker on 2012-02-16
After the last update, the menu shadows in my second monitor won't disappear. Everything works as expected in my first monitor.

My video drivers (Nvidia 295.x) have not changed recently, so I'm assuming this is a Compiz or Unity issue? Any tips?

[[IMG]http://img832.imageshack.us/img832/6503/52907334.th.png[/IMG]]("http://img832.imageshack.us/img832/6503/52907334.png")

---

### Post by ppd on 2012-02-16
that would be this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933624](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933624)

---

### Post by kyleabaker on 2012-02-16
> **ppd said:**
> that would be this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933624](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933624)

Awesome. Thanks!

---

### Post by dino99 on 2012-02-16
> **ppd said:**
> that would be this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933624](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933624)

there is a new compiz package since this report (ubuntu3)

---

### Post by ppd on 2012-02-16
> **dino99 said:**
> there is a new compiz package since this report (ubuntu3)

you're sure? I don't see any new build for precise.

---

### Post by williammanda on 2012-02-16
The shadows / outlines just started after the last update today. I'm using sandy bridge (whatever drivers that support that) on a single monitor.

---

### Post by grahammechanical on 2012-02-16
I have had these shadows since the last Compiz update but they soon change into the real thing.

---

