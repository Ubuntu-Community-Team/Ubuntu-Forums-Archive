---
title: "Limiting access to computer based on OTP"
date: 2010-08-16
forum: Security
---

### Post by shasderias on 2010-08-16
Not too sure where to post this, apologies if this is the wrong forum.

I am trying to limit access to the system unless authentication code (quite possibly an OTP code not unlike the ones used in internet banking) is given at a regular interval.

Been looking around and this does not seem to be a common question, would anyone have any insights on how this can be done? The most preferable solution is to force a logout to the lock screen and remain as such until the code is given.

Thanks!

---

### Post by Lars Noodén on 2010-08-23
You can hook one into PAM.

In Ubuntu, look at the package donkey, or opie-client + opie-server to start with. There are also commercial dongles like Yubikey.

---

