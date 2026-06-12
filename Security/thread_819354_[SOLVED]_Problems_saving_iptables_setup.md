---
title: "[SOLVED] Problems saving iptables setup"
date: 2008-06-05
forum: Security
---

### Post by kamaji792 on 2008-06-05
Hi all,

I have been using the excellent [IPTables HowTo](https://help.ubuntu.com/community/IptablesHowTo).

You are supposed to be able to save your current setup using the following command:
```
sudo iptables-save > /etc/iptables.rules
```
However when I try this I get the following:
```
-bash: /etc/iptables.rules: Permission denied
```
The really strange thing is I can edit the file directly with an editor (sudo vim /etc/iptables.rules).

Any ideas?

---

### Post by cdenley on 2008-06-05
sudo runs iptables-save as root, then you're piping the result of the sudo command as your regular user to /etc/iptables.rules. However, you don't have permission to create a file in /etc. This is the only annoying thing about sudo. Try this, instead.
```

sudo bash -c "iptables-save > /etc/iptables.rules"

```

---

### Post by kamaji792 on 2008-06-05
Just like the man said.

Thanks cdenley :)

---

### Post by ravingmad on 2010-05-18
Cool bananas .... thanks a mil :)

---

