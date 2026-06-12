---
title: "gpg key passphrase retrieval"
date: 2013-03-28
forum: Security
---

### Post by jon zendatta on 2013-03-28
Hello World

I created a GPG key 12 months ago. Now I'm updating my Launchpad details which requires my key & passphrase?
I have * Key ID
          * Key Fingerprint
For the life of me I cannot remember my passphrase. Any ideas or do I bruteforce?

Thanks for any suggestions:KS

---

### Post by kevdog on 2013-03-29
Brute force unless you know some other zero day exploit

---

### Post by jon zendatta on 2013-03-29
Bruteforce imm. Is it possible to have more than one GPG key and just ignore this one?:KS

---

### Post by kevdog on 2013-03-29
Sure you can always create another key on the keyring.  I have like 3 gpg keys myself.

---

### Post by sudodus on 2013-03-29
It is supposed to be hard to crack a gpg passphrase. But maybe tomorrow morning you'll remember it. Otherwise do as suggested, get a new key, and make a system to keep your passphrases and passwords safe.

- available for you but hidden from everybody else

---

### Post by tubbygweilo on 2013-03-29
jon, 
you may do well to consider making a revocation certificate for any new key you create. Keep it in a safe place not on you machine, it is not something you need all that often but when you need one you need it right now.

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Creating_a_revocation_key.2BAC8-certificate](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Creating_a_revocation_key.2BAC8-certificate)

---

