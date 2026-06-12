---
title: "[SOLVED] How to limit ssh access"
date: 2008-07-30
forum: Security
---

### Post by victorbrca on 2008-07-30
I'm trying to limit ssh access to one of my servers, but I can't seen to get it working via access.conf and hosts.deny/allow. Wondering if anyone can give me a hand. 

What I want to do is allow only one user to access from anywhere (any domain or IP), and all remaining users from local network only. 

Any ideas??


Thanks,

Vic.

---

### Post by unutbu on 2008-07-30
Have you tried

hosts.allow:
```
ALL : username@ALL
ALL : KNOWN@LOCAL
```

hosts.deny:
```
ALL : ALL
```

?

---

### Post by victorbrca on 2008-07-30
> **unutbu said:**
> Have you tried

hosts.allow:
```
ALL : username@ALL
ALL : KNOWN@LOCAL
```

hosts.deny:
```
ALL : ALL
```

?

No I haven't. This is what I was trying:

hosts.deny
```
sshd: ALL
```

hosts.allow
```
sshd: username : ALL
# or
sshd: username : *
```



Should I change the code you gave me with the following so it only blocks ssh?

hosts.deny
```
sshd: ALL
```

hosts.allow
```
sshd: user@ALL
sshd: LOCAL@xx.xx.xx.xx/xx
```

---

### Post by kebes on 2008-07-30
> **victorbrca said:**
> I'm trying to limit ssh access to one of my servers, but I can't seen to get it working via access.conf and hosts.deny/allow.

Is there any particular reason you are controlling it at the hosts.deny/allow level instead of at the SSH-config level? For instance, you can add options to the file "/etc/ssh/sshd_config" to restrict user access, like:
```

PermitRootLogin no
AllowUsers user1 user2@localhost user3@localhost user4@localhost

```
After reloading (sudo /etc/init.d/ssh reload), this will make it so that user1 can access from anywhere, and users user2, user3, and user4 can only access from local. Any other users cannot access at all. ([More info on AllowUsers]("http://www.freebsd.org/doc/en/books/handbook/openssh.html").)

---

### Post by victorbrca on 2008-07-30
> **kebes said:**
> Is there any particular reason you are controlling it at the hosts.deny/allow level instead of at the SSH-config level? For instance, you can add options to the file "/etc/ssh/sshd_config" to restrict user access, like:
```

PermitRootLogin no
AllowUsers user1 user2@localhost user3@localhost user4@localhost

```
After reloading (sudo /etc/init.d/ssh reload), this will make it so that user1 can access from anywhere, and users user2, user3, and user4 can only access from local. Any other users cannot access at all. ([More info on AllowUsers]("http://www.freebsd.org/doc/en/books/handbook/openssh.html").)


That works flawless!! Thanks a lot for the info! :)


Vic.

---

