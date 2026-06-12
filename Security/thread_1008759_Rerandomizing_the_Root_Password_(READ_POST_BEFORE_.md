---
title: "Rerandomizing the Root Password (READ POST BEFORE REPORTING PLEASE)"
date: 2008-12-11
forum: Security
---

### Post by setsanto on 2008-12-11
Hello Everyone,

I installed ubuntu last week, and due to my inexperience immediately created a password for root that I knew.  I was wonder is there any way to rerandomize the password now that I know about sudo and its various applications?

---

### Post by ibutho on 2008-12-11
You can lock the account again by doing,
```
sudo passwd -l root
```

---

### Post by bodhi.zazen on 2008-12-12
Actually , there is a small bug.

You should use:

```
sudo usermod --lock root
```

    [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

---

