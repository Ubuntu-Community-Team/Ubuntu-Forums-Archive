---
title: "if-up.d script problem"
date: 2011-04-16
forum: Server Platforms
---

### Post by vnv on 2011-04-16
Hi,

I am running Ubuntu server 10.10 and trying to setup iptables rules in /etc/if-up.d/iptables

> 
root@host# cat /etc/network/if-up.d/iptables

#!/bin/sh -e

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT



Problem is that iptables doesn't get updated and I don't see them when iptables -L is executed after reboot.

Could anybody give a hint where I am missing the point.

Tnx in advance.

---

### Post by dfreer on 2011-04-16
Not sure why if-up.d isn't working, haven't used it myself. You can however specify in your /etc/network/interfaces file:
```
pre-up /etc/if-up.d/iptables
```
Or post-up, depending on what you want it to do.

Also, I can't seem to find any reference to #!/bin/sh **-e**, do you know what the -e option does? All shell scripts I've seen/used are just #!/bin/sh.

---

### Post by vnv on 2011-04-16
Tnx it worked like a charm ):P

> 
I have copied bind script and -e was already there.... I've removed it because I also didn't find meaning for it.


tnx once more.

---

