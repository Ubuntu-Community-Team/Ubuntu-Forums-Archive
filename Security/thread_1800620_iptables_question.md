---
title: "iptables question"
date: 2011-07-09
forum: Security
---

### Post by jsvidyad on 2011-07-09
Hello, what do the following two commands do? Do they modify the iptables rules in any way?

sudo /sbin/iptables -L -n
sudo /sbin/ip6tables -L -n



Thank You!!!

---

### Post by haqking on 2011-07-09
> **jsvidyad said:**
> Hello, what do the following two commands do? Do they modify the iptables rules in any way?

sudo /sbin/iptables -L -n
sudo /sbin/ip6tables -L -n



Thank You!!!

it wont modify them, you are asking to list with a numeric output the entries in a given chain, you haventr specified a chain so it should list all ?

---

### Post by jsvidyad on 2011-07-29
They only list the iptables rules right?? Do they modify anything at all?

---

### Post by Lars Noodén on 2011-07-29
They don't modify anything.

---

### Post by kimda on 2011-07-29
If you want to test out iptables rules and are not sure. You can use iptables-apply

from:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

NOTE: With iptables 1.4.1.1-1 and above, a script allow you to test your new rules without risking to brick your remote server. If you are applying the rules on a remote server, you should consider testing it with: 
```
# iptables-apply /etc/iptables.rules

``` 


After testing, if you have not added the iptables-save command above to your /etc/network/interfaces remember not to lose your changes: 

```
# iptables-save > /etc/iptables.rules
```

---

### Post by Lars Noodén on 2011-07-29
> **kimda said:**
> If you want to test out iptables rules and are not sure. You can use iptables-apply

"[If the new ruleset cut the existing connection, the user will not be able to answer affirmatively.](http://manpages.ubuntu.com/manpages/natty/en/man8/iptables-apply.8.html)"

Cool.  Is there a way to test what will happen to different sorts of packets?  ipchains used to have the -C option to check how the rules would handle a specific packet.  Does something similar exist for IP Tables?

---

