---
title: "Is there a file which remembers all users passwords"
date: 2007-08-24
forum: Server Platforms
---

### Post by bggashnik on 2007-08-24
I wannna ask if I login in the console as root,is there a file that I can open and see the administrator's password?

---

### Post by olejorgen on 2007-08-24
I don't think so. It's a file called /etc/passwd and /etc/shadow that contains user info, but I think the password bit is an secure hash/encrypted. (Please confirm?)

---

### Post by sonofusion82 on 2007-08-24
> **olejorgen said:**
> I don't think so. It's a file called /etc/passwd and /etc/shadow that contains user info, but I think the password bit is an secure hash/encrypted. (Please confirm?)


yes, they are hashed. and not easily reversible to reveal the actual password unless you have large amount of computing resources to mount a brute-force attack.. well, sometimes dictionary attack may work...

---

