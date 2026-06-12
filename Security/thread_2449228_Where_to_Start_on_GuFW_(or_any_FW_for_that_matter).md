---
title: "Where to Start on GuFW (or any FW for that matter)"
date: 2020-08-22
forum: Security
---

### Post by ceyarrecks on 2020-08-22
alas, it has been too many years since I dabbled, but in having recently installed Ubuntu Kitty v20, and enabled GuFW, I would like more granular control then what I find in Gufw.
(I read through as best I could the sticky on "Is FW needed,...")

Although, I am not exactly sure what I am asking for to be able to do a specific word/phrase search.
In essence, I would prefer to have GuFW to prompt me whenever X, Y, or Z program/service/etc attempts a network connection, to then Allow, Deny, etc.
Additionally, a prompt that would give announcement and ability to prevent Program A from launching program B would be nice too.

Help with the above terminology would also be appreciated. 
If I recall correctly, I would prefer to have a **Restrictive **Firewall (BLOCK _Everything_, then Allow as Needed) then train/configure it as needed as network connection attempts are discovered; rather than blindly guessing about a, b, or c protocols, or closing the "barn door" *after* the horses have fled.

Are these functions available in general? and if not, why not?
Also, can Gufw be configured to perform as such, or need I interact with a different GUI-based FW?

Thank you for your time in thoughtfully replying.

---

### Post by kevdog on 2020-08-22
From your description I think you wanting a more "application" based firewall than a port based firewall.  UFW/iptables/GUFW are "port" based firewalls where you deny/allow things based on port/IP address etc.  You can also by default block outgoing connections but I don't think any of these tools is going to give you pop up info on what is being blocked.  Usually creating firewall rules for port based firewalls takes a bit of fine tuning -- start with a base set of rules and then try using applications while at the same time keeping a good eye on the firewall logs to see what ports/IP addresses are being accessed.  It can definitely be a laborious process.  

I know there are a few application based firewalls for Linux however honestly I can't think of the name of any of them off the top of my head.  Usually these projects get going and then kind of lose some steam during the development process after awhile.  I'm sure someone will chime in on this thread naming a few.  I'm not sure how well they work however. The "port" based firewall types are generally considered the default gold standard.

---

### Post by EuclideanCoffee on 2020-08-22
Douane may be the only viable option though it's not supported yet in the Ubuntu archives at all.

Here's some information on that application firewall.

[https://gitlab.com/douaneapp/Douane](https://gitlab.com/douaneapp/Douane)

However, generally firewalls work best in layers since anything infecting the host can simply disable a firewall. Best of luck.

---

