---
title: "Keep getting blocked in hosts.deny"
date: 2008-02-13
forum: Server Platforms
---

### Post by Juzz on 2008-02-13
I have a problem that one of my machines keep getting blocked in the hosts.deny on my server:

```
SSHD: 192.168.1.8
```

I have even added this to my hosts.allow:

```
ALL: 192.168.1.8
```

However each time I restart either sshd or denyhosts then my machines IP address keeps popping up in hosts.deny.

Can anyone tell me how to get out of that?

---

### Post by Juzz on 2008-02-13
I now updated my hosts.allow with a carriage return at the end of the line - and lo and behold - it now works :lolflag:

---

### Post by MJN on 2008-02-13
However, is the address still in hosts.deny? When I used to use Denyhosts it used to be a bit of a pig to remove banned addresses that got accidentally caught as you need to remove them from the Denyhosts tracking files, rather than hosts.deny, otherwise if you manually remove it from the latter it will just put them back in.

I later moved to Fail2Ban - much simpler! ;)

Mathew

---

