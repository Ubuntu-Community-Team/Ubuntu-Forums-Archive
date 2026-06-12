---
title: "Issue with ssh into my server"
date: 2014-10-03
forum: Server Platforms
---

### Post by grier-devon on 2014-10-03
So I am trying to ssh into my Ubuntu server and I get this......

```
 ssh root@198.XXX.XX.XXX@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
5e:59:81:d1:b9:e5:05:38:36:4e:9f:8e:95:db:2e:d1.
Please contact your system administrator.
Add correct host key in /home/devon/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/devon/.ssh/known_hosts:1
  remove with: ssh-keygen -f "/home/devon/.ssh/known_hosts" -R 198.XXX.XX.XXX
ECDSA host key for 198.XXX.XX.XXX has changed and you have requested strict checking.
Host key verification failed.
```

How do I fix this?

---

### Post by Doug S on 2014-10-03
This happens to me often, but I always know why (i.e. made a new computer with the same name and IP as some old one; or have a dual installation; or...).
Have you made some change that would explain why you are getting this message?

Anyway, the message itself tells you how to fix it, so I'm not suite sure what you are asking for.

---

### Post by grier-devon on 2014-10-04
No I haven't made any changes, I read the error a little more closely and seen what you are saying and fixed it. I just never seen that error before and this is my first Ubuntu server and I don't want to mess it up. Thanks for the response.

---

### Post by Doug S on 2014-10-04
Glad you got it fixed.> **grier-devon said:**
> No I haven't made any changes,...I just want to emphasize, and for your own security peace of mind, it is important to understand why the message occurred in the first place. If you were establishing a new ssh session from the same computer as always and nothing changed but you got the identification has changed error, then there is a security concern.

---

