---
title: "If a standard account gets hacked, can administrator account get hacked from there?"
date: 2019-09-08
forum: Security
---

### Post by linux-user-0987 on 2019-09-08
I know there are different types of attacks that give different level of access.
So the question is, are there attacks which can be done to a standard account that give administrator or root access?


Is there some way this can be prevented like using a yubikey? Once I log out of the hacked account and access the administrator account I can use the yubikey to do sudo tasks. Would this way protect the administrator account.

Is there some other way to ensure administrator/root account does not get accessed from a hacked standard account? The hard drive is shared so does that cause a problem?

What about other standard accounts? 

I know I can use virtual box and thats what I am thinking of doing inside a standard account but it is possible the hacker might break out of it.

---

### Post by sevendogs1337 on 2019-09-08
Yes, it's called privilege escalation.  If no remote access,  the attacker would have to have local access.

---

### Post by linux-user-0987 on 2019-09-08
> **sevendogs1337 said:**
>   If no remote access,  the attacker would have to have local access.

What do you mean by local access?

---

### Post by sevendogs1337 on 2019-09-09
Sorry, I meant physical access.

---

