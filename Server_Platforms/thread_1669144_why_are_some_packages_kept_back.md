---
title: "why are some packages kept back?"
date: 2011-01-17
forum: Server Platforms
---

### Post by guest_user on 2011-01-17
using ubuntu server edition 10.04.
1) when I do apt-get update and apt-get upgrade, it says some packages namely, the kernel packages are kept back, why is this? 

2) would upgrading these packages break my system?

3) how do I go about upgrading these packages?

---

### Post by wojox on 2011-01-17
Do a 

```
sudo apt-get dist-upgrade
```

---

### Post by guest_user on 2011-01-17
but would doing that break my system?

---

### Post by snowpine on 2011-01-17
> **guest_user said:**
> but would doing that break my system?

If the new kernel "breaks your system" you can simply reboot and choose the old kernel from the GRUB boot menu.

---

### Post by Thirtysixway on 2011-01-17
> **guest_user said:**
> but would doing that break my system?

Probably not. :popcorn: They usually don't.

---

