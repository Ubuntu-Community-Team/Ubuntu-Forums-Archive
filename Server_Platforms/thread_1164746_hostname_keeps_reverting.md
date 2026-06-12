---
title: "hostname keeps reverting"
date: 2009-05-19
forum: Server Platforms
---

### Post by bluethundr on 2009-05-19
I built a machine that was originally called 'web3'. The client requested that it be renamed 'stage'.

so I logged in and issued the command:

```


# hostname stage


```

then issued

```


# hostname


```

to make sure it changed.

lately, it keeps reverting to the name 'web3'. why?

this is confusing!

---

### Post by comandrei on 2009-05-20
Did you try editing /etc/hostname as root?

---

