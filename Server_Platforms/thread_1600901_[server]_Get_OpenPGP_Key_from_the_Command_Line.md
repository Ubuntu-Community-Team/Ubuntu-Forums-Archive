---
title: "[server] Get OpenPGP Key from the Command Line"
date: 2010-10-19
forum: Server Platforms
---

### Post by Zanthir on 2010-10-19
I was just having some trouble getting an OpenPHP Key on Ubuntu Server. The link from Launchpad said, "go to applications..." but I'm not using a desktop environment, so I had to go to [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto) to learn how. Basically it boiled down to this:
 
```
gpg --cert-digest-algo=SHA256 --default-preference-list="h10 h8 h9 h11 s9 s8 s7 s3 z2 z3 z1 z0" --gen-key
1
[return]
[return]
y
Fname Lname
email@address.com
[return]
Enter your passphrase.
Enter your passphrase.

```That is basically what I entered each time, but at the end it would freeze because it didn't have enough random bytes.
 
Can anyone help?

---

### Post by McNils on 2010-10-19
you need to do something when creating the key. I created a key running find / and typing on the keyboard during key generation.

---

