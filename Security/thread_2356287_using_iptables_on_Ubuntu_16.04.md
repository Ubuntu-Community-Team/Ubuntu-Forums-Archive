---
title: "using iptables on Ubuntu 16.04"
date: 2017-03-21
forum: Security
---

### Post by sniper8752 on 2017-03-21
I have iptables installed.  I don't see the iptables file in /etc.  Also, when I apply a rule, and reboot, those changes are not saved and applied.  How do I fix this?

---

### Post by &amp;KyT$0P# on 2017-03-21
What file in /etc ?

I just manually save the rules somewhere -
```
sudo bash -c 'iptables-save > saved_iptables'
```
... then add this to [FONT=Courier New]/etc/rc.local[/FONT] (**before** the "exit 0" line) to restore the rules after reboot.
```
cat /full/path/to/saved_iptables | iptables-restore
```

Does it work for you?

---

### Post by sniper8752 on 2017-03-22
Yes, that worked; thank you.

---

### Post by &amp;KyT$0P# on 2017-03-22
You're welcome. :KS

---

