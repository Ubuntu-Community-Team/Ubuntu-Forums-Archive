---
title: "why does ubuntu LTS package pre-release and apha software?"
date: 2018-05-13
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2018-05-13
I understand that LTS is supposed to be stable for production, yet some packages in the official channel of 18.04 are pre releases e.g mesa is at versio 18.00rc5 and just got a bunch of errors trying to compile some program with libglm-dev. The version is 0.99~a2-2, presumably an alpha, the stable release is 0.9.8-5 I am sure there are others.

What is the reason of including alpha software in the LTS?

---

### Post by kerry_s on 2018-05-14
ubuntu pulls from debian sid, then freezes it, only updating for security.

so i can only assume that's what was in the repo. unless there a security reason it will most likely stay at  0.99~a2-2 until lts eol

---

