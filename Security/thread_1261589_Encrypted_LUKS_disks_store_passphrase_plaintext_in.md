---
title: "Encrypted LUKS disks store passphrase plaintext in memory"
date: 2009-09-08
forum: Security
---

### Post by ufbournutmus on 2009-09-08
Does anyone know if this bug was ever fixed: [https://bugs.launchpad.net/ubuntu/+bug/196368](https://bugs.launchpad.net/ubuntu/+bug/196368)

---

### Post by ufbournutmus on 2009-09-09
Bump.

What does this bug mean, by the way? Does it mean someone can get my password upon bootup?

---

### Post by bodhi.zazen on 2009-09-10
There have been reports of recovering your LUKS password from RAM and from ram after re-booting as you describe yes.

[coldboot.pdf (application/pdf Object)]("http://citp.princeton.edu/pub/coldboot.pdf")

---

### Post by ufbournutmus on 2009-09-17
> **bodhi.zazen said:**
> There have been reports of recovering your LUKS password from RAM and from ram after re-booting as you describe yes.

[coldboot.pdf (application/pdf Object)]("http://citp.princeton.edu/pub/coldboot.pdf")


Do you mean you could shut down a computer, and someone could come back 30 minutes later, reboot it and get the password from the RAM? What is the point of the encryption then?

---

### Post by rookcifer on 2009-09-17
> **ufbournutmus said:**
> Do you mean you could shut down a computer, and someone could come back 30 minutes later, reboot it and get the password from the RAM? What is the point of the encryption then?

No, not 30 minutes.  More like 1 to 2 minutes maximum.  And even then, the adversary needs a way to keep the RAM cold (that's why it's called "cold boot").  This can be achieved with canned air or something of that sort.  If you read the technical paper, you will see that they explain this.

Moral of story:  If you are the only one with physical access to the machine (within a couple of minutes of it shutting down) then you have nothing to worry about.  Once the RAM is off for a few minutes, this attack is worthless.

---

