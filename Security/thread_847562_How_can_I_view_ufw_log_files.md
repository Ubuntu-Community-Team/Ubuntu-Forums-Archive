---
title: "How can I view ufw log files?"
date: 2008-07-02
forum: Security
---

### Post by kansasnoob on 2008-07-02
I'm fully aware that what I'm doing is just fiddling around, OK?

I'm quite accustomed to Firestarter and know how to view that log, and I'm also aware that for the most part there is no need to view any log at all other than the iptables log, so this is a want ........ not a need! Suffice it to say I like to fiddle around:-({|=

So I know I can enable ufw by 

```
sudo ufw enable
```

and enable logging by

```
sudo ufw logging on
```

Where I get lost is how to view the ufw log! Or is it even different from the iptables log:confused:

---

### Post by kansasnoob on 2008-07-02
With fwlogwatch & postfix installed I can get the following by just running:

```
sudo fwlogwatch
```

Still not quite what I'm looking for.

[ATTACH]76172[/ATTACH]

---

### Post by beetlejuice_masterson on 2009-09-30
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

cat /var/log/messages | grep UFW

---

