---
title: "apt-get &quot;blacklist&quot;?"
date: 2007-09-02
forum: Repositories &amp; Backports
---

### Post by apetresc on 2007-09-02
I'm running Ubuntu on a Xen VPS, remotely hosted. It used to be running Breezy, which is obviously no longer available, so I did a dist-upgrade to Dapper. The problem is that, because of the unique setup those guys have, Dapper's version of udev breaks everything. Is there a way I can somehow "blacklist" udev so that running apt-get dist-upgrade will upgrade every package *except* udev?

Thanks in advance, guys :)

---

### Post by exploder on 2007-09-02
Highlight the package in Synaptic, then go to "Package" and check "Lock Version".

---

### Post by apetresc on 2007-09-02
> **exploder said:**
> Highlight the package in Synaptic, then go to "Package" and check "Lock Version".
Unfortunately, this server does not have X installed, let alone Synaptic, so this is not possible for me.

However, if it can be done through Synaptic, I imagine it is also probably possible through aptitude! I just don't know how. :(

---

### Post by Seisen on 2007-09-02
Try this ```
 sudo aptitude udev=
```

---

