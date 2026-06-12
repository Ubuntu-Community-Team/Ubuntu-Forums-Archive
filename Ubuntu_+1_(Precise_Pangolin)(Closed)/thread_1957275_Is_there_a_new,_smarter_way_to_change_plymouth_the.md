---
title: "Is there a new, smarter way to change plymouth themes?"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-04-12
I'm still using:

```
sudo update-alternatives --config default.plymouth
```

Followed by:

```
sudo update-initramfs -u
```

I have found some gui-tools that can be added via PPA, but I really prefer CLI. Just wondering if I've missed anything about the prescribed method of changing plymouth themes.

---

### Post by kansasnoob on 2012-04-13
Bump ;)

---

### Post by xyzzyman on 2012-04-14
That seems to be the exact way. You're changing the theme by the first command, and the second one actually applies the change to the boot process. What were you thinking that could be done "smarter"?

---

### Post by kansasnoob on 2012-04-14
> **xyzzyman said:**
> That seems to be the exact way. You're changing the theme by the first command, and the second one actually applies the change to the boot process. What were you thinking that could be done "smarter"?

No idea, I missed a great deal of the Oneiric dev cycle so I'm continually learning new stuff.

---

