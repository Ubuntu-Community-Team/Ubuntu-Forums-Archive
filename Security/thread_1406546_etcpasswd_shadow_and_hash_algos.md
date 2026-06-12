---
title: "etc/passwd shadow and hash algos"
date: 2010-02-14
forum: Security
---

### Post by shadowbound on 2010-02-14
Hey.

I was wondering where the setting are in Ubuntu (running 9.10 right now), that specify whether to store the password in the shadow or passwd file, and what algorithm is used to encrypt it. I seem to remember that it should support MD5, SHA-256, SHA-512 DES, and maybe a few others. By default the passwords are shadowed and use sha512, however how do you change these things around? 

Best regards.

---

### Post by Agent ME on 2010-02-14
I'm not sure if these are easily configurable, but I was wondering, why would you want to change these settings? Moving the hashes to /etc/passwd gives no benefit at all, and allows any user to obtain the hashes which they can then attempt to bruteforce. The sha512 password algorithm has no weaknesses I know of, and I would think that most of everything else would be a step down from it.

---

