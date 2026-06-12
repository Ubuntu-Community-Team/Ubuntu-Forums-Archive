---
title: "Save Iptables Rules"
date: 2009-06-22
forum: Server Platforms
---

### Post by ae7@live on 2009-06-22
[CENTER][COLOR="Red"][SIZE="4"][FONT="Comic Sans MS"]Hi,
I am Asking For How I save My current iptables rules beacaus evry time i restart the server i had to rewrite it back
i made alot of sraches but almost results was for Fedora as 
 /etc/sysconfig/iptables
#-o
Thanks [/FONT][/SIZE][/COLOR][/CENTER]

---

### Post by madverb on 2009-06-22
I'd be looking through logs to see why the rules are being flushed on a restart.
The rules shouldn't be lost on a restart.

---

### Post by Bachstelze on 2009-06-22
> **madverb said:**
> I'd be looking through logs to see why the rules are being flushed on a restart.
The rules shouldn't be lost on a restart.

What? Of course iptable rules are lost on reboot...

@op

```
iptables-save > rules.txt
#Then to restore the saved rules after a reboot:
iptables-restore < rules.txt
```

---

### Post by madverb on 2009-06-23
I seriously never knew that. Is there an init script in Ubuntu that can reset them each reboot?

Edit:
Alternatively you could add the iptables-restore and iptables-save to the if-pre-up.d and if-post-down.d directories in the /etc/network directory instead of modifying /etc/network/interface directly.

The script /etc/network/if-post-down.d/iptasave will contain:

#!/bin/sh
iptables-save -c > /etc/iptables.rules
exit 0

and /etc/network/if-pre-up.d/iptaload will contain:

#!/bin/sh
iptables-restore < /etc/iptables.rules
exit 0

Then be sure to give both scripts execute permissions:

sudo chmod +x /etc/network/if-post-down.d/iptasave
sudo chmod +x /etc/network/if-pre-up.d/iptaload

**Why isn't that in by default?**

---

### Post by Bachstelze on 2009-06-23
> **madverb said:**
> 
**Why isn't that in by default?**

Why should it be?

---

### Post by kamaji792 on 2009-06-23
More for general information but I found the following link useful in understanding IP Tables and how to save them and restore them at start up.

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

atb

---

### Post by madverb on 2009-06-23
It's usually fairly normal to save a configuration after you have entered it into the system. Why would you want to lose it after a reboot?

---

### Post by ae7@live on 2009-06-24
Thanks Everyone For Help

---

