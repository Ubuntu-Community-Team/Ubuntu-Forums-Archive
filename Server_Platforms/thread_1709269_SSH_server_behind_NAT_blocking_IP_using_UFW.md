---
title: "SSH server behind NAT blocking IP using UFW"
date: 2011-03-18
forum: Server Platforms
---

### Post by hawk2010 on 2011-03-18
Hi,

I have a SSH server on Ubuntu 10.04 running behind a NAT. I have done the port-forwarding at the router. However say for example I want to restrict people connecting to the SSH server by country IP's. When I configure ufw with the following rule it still lets the IPs that are restricted through. Any idea why

sudo ufw allow from xxx.xxx.xxx.xxx/24 to any port 2556

Your help is much appreciated.

---

### Post by BkkBonanza on 2011-03-18
Well, perhaps because you are telling it to allow rather than deny. You need to tell it to deny an IP range as saying allow doesn't block anything. If you only want one range only then deny all and then allow that range.

sudo ufw default deny
sudo ufw allow from xxx.xxx.xxx.xxx/24 to any port 2556

---

### Post by hawk2010 on 2011-03-18
Hi.
but by default ubuntu blocks all inbound connections :-|

> **BkkBonanza said:**
> Well, perhaps because you are telling it to allow rather than deny. You need to tell it to deny an IP range as saying allow doesn't block anything. If you only want one range only then deny all and then allow that range.

sudo ufw default deny
sudo ufw allow from xxx.xxx.xxx.xxx/24 to any port 2556

---

### Post by BkkBonanza on 2011-03-18
I'm don't think that's the case. UFW just acts as a interface to iptables and iptables doesn't have any default deny rules. It is true that Ubuntu doesn't have any ports open by default and hence nothing can connect, but iptables doesn't explicitly block ports unless configured for that.

Have a look at this post: [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

(UFW just adds a simplified rule set for iptables and I've always used iptables directly as I don't find the native syntax that, umm, taxing.)

---

### Post by hawk2010 on 2011-03-18
Actually that's not true. I just powered up squid with ufw enable and when i try to access the 3128 port I cannot but if I do ufw allow 3128, then it get through.  Even the man ufw states the following :(

"On installation, ufw is disabled with a default incoming policy of deny
       and  a default outgoing policy of allow, with stateful tracking for NEW
       connections. Having a default policy of allow without stateful tracking
       can   be  achieved  by  using  ACCEPT_NO_TRACK  instead  of  ACCEPT  in
       /etc/defaults/ufw"

---

### Post by BkkBonanza on 2011-03-18
Hmm. Seems to be some conflicting info. This Ubuntu docs page says otherwise...

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

"Unless you have set the default to deny when you initially enable ufw, it is in ALLOW mode and will allow everything incoming and outgoing until you make rulesets. "

Given your original question I thought it made sense it didn't deny anything.

---

