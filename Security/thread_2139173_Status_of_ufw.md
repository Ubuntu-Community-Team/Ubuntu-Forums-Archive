---
title: "Status of ufw"
date: 2013-04-26
forum: Security
---

### Post by jsvidyad on 2013-04-26
Hello,

  How do I find the status of the ufw firewall(i.e. whether it's active or inactive) and also how can I list the ufw firewall rules that have been set?

---

### Post by slickymaster on 2013-04-26
> **jsvidyad said:**
> Hello,
  How do I find the status of the ufw firewall(i.e. whether it's active or inactive) and also how can I list the ufw firewall rules that have been set?
```
sudo ufw status
```
Will tell you if ufw is enabled or disabled and also list the current ufw rules that are applied to your iptables.

---

### Post by OrangeCrate on 2013-04-26
> **jsvidyad said:**
> Hello,

  How do I find the status of the ufw firewall(i.e. whether it's active or inactive) and also how can I list the ufw firewall rules that have been set?

Here you go:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

