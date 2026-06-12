---
title: "stdin: is not tty"
date: 2015-04-11
forum: Ubuntu Development Version
---

### Post by orj-gmail on 2015-04-11
Via passwd root, I made it possible to log in as root to ubuntu gnome. I did this in other releases before too. Sometimes it is useful or practical to have this possibility. But now after log in, I get the following error message:

Error found
When loading /root/.profile
stdin: is not tty
As result the session will not configured correctly.
You should fix it to solve the problem as soon as feasible.

Anyone encountered the same? I never had this before. After the error message I can continue as root.

---

### Post by dino99 on 2015-04-11
you should not be root by default but only using an user session. Dont open all the doors to spyers for your own security

---

### Post by coffeecat on 2015-04-11
Don't log in to a graphical desktop as root - problem solved. It is neither useful nor practical nor sensible. 

Some reading material for you:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by orj-gmail on 2015-04-11
> **9d9 said:**
> you should not be root by default but only using an user session. Dont open all the doors to spyers for your own security

I know this and I don't use root by default only in a very few occasions from time to time. But I don't know the meaning of this errror message and what to do to solve the problem causing it.

---

### Post by coffeecat on 2015-04-11
Please clarify - are you logging into a GUI desktop as root?

---

### Post by zika on 2015-04-11
> **coffeecat said:**
> Don't log in to a graphical desktop as root - problem solved. It is neither useful nor practical nor sensible. 

Some reading material for you:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)Message and problem are easily solvable. But, honoring warning given above I'll refrain from giving any details. This, sort of, is not a bug but kind of bug/feature depending from he point of view of spectator. Well documented on wast net.

---

