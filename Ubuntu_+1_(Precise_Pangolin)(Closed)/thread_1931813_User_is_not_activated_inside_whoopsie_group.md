---
title: "User is not activated inside whoopsie group"
date: 2012-02-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-02-26
I was wondering why some crashes i get inside /var/crash/ was owned by "user" & others not. And checking the properties i've found that /var/crash/ is owned by whoopsie only (in fact root:whoopsie).

To my point of view ALL the crashes should be owned by "user".

---

### Post by jpeddicord on 2012-02-26
Some crash logs contain sensitive information, and on a multi-user system, you don't want just anyone to be able to get at them. So system crashes are owned by root, your own crashes are yours, and other users' crash dumps are owned by themselves. All crashes are in the "whoopsie" group so that the crash daemon can access them.

---

### Post by dino99 on 2012-02-26
> **jpeddicord said:**
> Some crash logs contain sensitive information, and on a multi-user system, you don't want just anyone to be able to get at them. So system crashes are owned by root, your own crashes are yours, and other users' crash dumps are owned by themselves. All crashes are in the "whoopsie" group so that the crash daemon can access them.

well i'm having some "synaptic" crashes lately and they are all owned by root. So if the logged user is the admin, such crashes dont have to be locked.

---

