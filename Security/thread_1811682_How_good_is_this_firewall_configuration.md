---
title: "How good is this firewall configuration?"
date: 2011-07-25
forum: Security
---

### Post by arroy_0209 on 2011-07-25
I am using Ubuntu 10.04 LTS. My firewall configuration is this:
Firewall enabled
Incoming: Deny
Outgoing: Allow
Preferences: Log option:
Enable ufw, gufw logging, set level: low
I have not added any rule

Can anybody please tell me if this is a reasonably good firewall configuration. Should I change the set level to high? My intention is to remain secure all the time (I need to avoid keylogger, spyware etc and be free from worries).  I have not yet added noscript, Adblock plus and safe history.


Second, In firefox preferences, I am unable to see the cookies option which I want to deny. Can anybody please help me?
Thanks.

---

### Post by bodhi.zazen on 2011-07-25
Those settings are sufficient for 99.99 % of people.

You really should read the security sticky, this is not windows, and the things you list are non issues in Linux, unless you install and configure a key logger yourself.

---

### Post by dirghrabadia on 2011-07-25
> **arroy_0209 said:**
> Second, In firefox preferences, I am unable to see the cookies option which I want to deny. Can anybody please help me?
Thanks.

You should be able to do that from Edit->Preferences->Privacy.

---

### Post by haqking on 2011-07-25
> **arroy_0209 said:**
> I am using Ubuntu 10.04 LTS. My firewall configuration is this:
Firewall enabled
Incoming: Deny
Outgoing: Allow
Preferences: Log option:
Enable ufw, gufw logging, set level: low
I have not added any rule

Can anybody please tell me if this is a reasonably good firewall configuration. Should I change the set level to high? My intention is to remain secure all the time (I need to avoid keylogger, spyware etc and be free from worries).  I have not yet added noscript, Adblock plus and safe history.


Second, In firefox preferences, I am unable to see the cookies option which I want to deny. Can anybody please help me?
Thanks.


+1 for what Bodhi said above me.

but also remember as a desktop user i suspect you are behind some type of router that accesses the internet.

Set the firewall on there and save the resources from your desktop unless you feel you need them (as said this is not windows).

router firewalls are usually linux based anyways so cause it is the linux kernel it has the netfilter firewall hardcoded into it anyways  and configured through a few checkboxes on the router interface.

---

