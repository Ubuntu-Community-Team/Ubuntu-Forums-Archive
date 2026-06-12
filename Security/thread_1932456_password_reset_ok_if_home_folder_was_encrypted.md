---
title: "password reset ok if home folder was encrypted?"
date: 2012-02-27
forum: Security
---

### Post by goodbye-windows(tm) on 2012-02-27
Hi,

For some unknown reason, I can't login to my system this morning. It keeps asking me for the password, but it rejects my password and asks me again, etc.

I can use the guest account th though.

**I need to do a password reset to get control of my primary account. If I use the reset procedure, won't my  encrypted home folder become unavailable???**

Also, is it possible that someone with physical access to my computer already (covertly) reset my password......can this explain why I can't login now???

I'm running xubuntu 11.10 with encrypted home folder on a P4 processor system (homebuilt) using MSI motherboard.

TIA

Art

---

### Post by Ms. Daisy on 2012-02-27
It's simple to reset your password. Just follow this tutorial.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by ztux on 2012-02-28
> **goodbye-windows(tm) said:**
> **I need to do a password reset to get control of my primary account. If I use the reset procedure, won't my  encrypted home folder become unavailable???**

Yes, that's the whole point. Your home directory is not encrypted with your login password, the encryption key is encrypted with the login password and decrypted on login.

If you reset your password, you will lose all the data in your home directory unless you made a backup of the key. If you didn't, then that data was lost the second you forgot your password.

---

