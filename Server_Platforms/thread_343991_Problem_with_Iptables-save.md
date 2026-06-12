---
title: "Problem with Iptables-save"
date: 2007-01-22
forum: Server Platforms
---

### Post by Claudiof on 2007-01-22
Hi,

When i'm trying to save my iptables configuration to /etc/ it gives me permission denied

[INDENT]krusty@barney:~$ sudo iptables-save > /etc/iptables.up.rules
-bash: /etc/iptables.up.rules: Permission denied[/INDENT]

But... why?

---

### Post by Claudiof on 2007-01-25
bump :|

---

### Post by JamieC on 2007-01-25
Use this instead:
```

sudo iptables-save > sudo /etc/iptables.up.rules

```

---

### Post by Claudiof on 2007-01-25
Nope :|

> krusty@barney:~$ sudo iptables-save > sudo /etc/iptables.up.rules
Unknown arguments found on commandlinekrusty@barney:~$

---

### Post by mannheim on 2007-01-25
Try (?) ```
sudo sh -c "iptables-save > /etc/iptables.up.rules"
```

---

### Post by Claudiof on 2007-01-25
Big thanks :)

---

