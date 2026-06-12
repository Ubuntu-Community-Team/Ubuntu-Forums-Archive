---
title: "iptables is empty"
date: 2005-03-30
forum: Server Platforms
---

### Post by CrustyDOD on 2005-03-30
Hey, if i issue command: sudo iptables --list, all i get is:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Is it just me or a lot of rules are missing?
I haven't played with rules but can  [this topic](http://ubuntuforums.org/showthread.php?t=22924) be a problem to this?

How do i re-set the firewall rules as they were on installation? Is there a list of these rules somewhere? If so, where do i save this list to work?

---

### Post by alastair on 2005-03-30
"iptables" is quite low-level, but many people make their own chains and add rules/targets manually (or via a script etc.) using the "iptables" command.

The question is : what generated your original rules?

firestarter? shorewall?

---

### Post by ola on 2005-03-30
I recomend firestarter if You are "just" into getting it up and running.. I have made a script that I used to use, but I actually never learned IPtables good enough..

---

### Post by CrustyDOD on 2005-03-30
hehe no worries then :)

---

