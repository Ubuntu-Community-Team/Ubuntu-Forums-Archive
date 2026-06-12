---
title: "Question about Apache2 and AppArmor"
date: 2010-11-09
forum: Security
---

### Post by TheAlien on 2010-11-09
In the most common AppArmor profiles for Apache2, these are allowed:

/bin/bash rmix,
/dev/tty rw,

Why? Because I deleted those two lines from my Apache2 profile, and Apache2 still runs flawlessly without any problems or errors.

---

### Post by artie_effim on 2010-11-09
Please post output from ```
sudo apparmor_status
```

---

### Post by TheAlien on 2010-11-09
> **artie_effim said:**
> Please post output from ```
sudo apparmor_status
```

It's an Ubuntu Server box, so it's difficult to copy and paste from that box to this one. But Apache2 is running in enforce mode under apparmor, another enforce mode appears in apparmor_status when Apache2 starts.

---

