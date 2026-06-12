---
title: "Basic security?"
date: 2007-03-12
forum: Server Platforms
---

### Post by FuzzMaster on 2007-03-12
I'm a bit concerned. I don't know crap-all about Linux security, except not to use root (though I use an account that has administrative powers, should I maybe flick that off?). Anyways, a friend of mine is aspiring moron hacker, and while I'm not aware if he can do any damage, I'm just curious if there's anything I can do to lower the risk of him, or others, from damaging anything. Can I block his IP or anything (he claims he's 'in' my system, and shows up in netstat)?

---

### Post by Mr. C. on 2007-03-12
Do you have a firewall ?

---

### Post by FuzzMaster on 2007-03-12
No, I do not.

---

### Post by Motoxrdude on 2007-03-12
Get a firewall.
```
sudo apt-get install firestarter
```

---

### Post by Mr. C. on 2007-03-12
I'd even recommend a standalone, commodity router/firewall.  They are essentially secure out of the box, and provide the extra layer of protection.  Today's firewall / routers are so cheap there simply is no reason not to have perimeter protection.

We can't even begin to discuss "basic security" without a firewall in place.

MrC

---

