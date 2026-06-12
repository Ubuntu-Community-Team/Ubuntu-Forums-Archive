---
title: "PGP key needs transferring"
date: 2011-05-07
forum: Security
---

### Post by redbikemaster on 2011-05-07
I had my system on a 80GB HDD. My primary is now a 20GB HDD with the 80GB as a slave. I want to know if I can transfer my PGP Personal key into my new install.

I am running 11.04 (Ubuntu) on the 20GB. I was running 10.10, tried to upgrade via the internet and that failed, so I switched hard drives. However, I have not deleted anything from the 80GB. It is connected and mounted as a slave.

---

### Post by rookcifer on 2011-05-08
PGP key or GPG key?

---

### Post by redbikemaster on 2011-05-08
The key that the 'Passwords & Encryption Keys' produces.

---

### Post by rookcifer on 2011-05-08
> **redbikemaster said:**
> The key that the 'Passwords & Encryption Keys' produces.

Just look in your /home directory and find the .gnupg folder.  Copy that folder and then transfer it to your new install.

---

### Post by redbikemaster on 2011-05-08
Sweet. Mission accomplished. Thanks.

---

