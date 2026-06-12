---
title: "does firestarter (software firewall) protect out of the box?"
date: 2010-09-15
forum: Security
---

### Post by webdevelopment on 2010-09-15
i was wondering if firestarter (software firewall) works out of the box or does it need some kind of configuration in order for it to provide protection?

is firestarter even needed with ubuntu?

---

### Post by damatta on 2010-09-15
It should require some configuration so that it protects you properly.
eg:services running that should be allowed, icmp packets to be accepted, DHCP,etc
Personally i like GUFW best...

---

### Post by webdevelopment on 2010-09-15
> **damatta said:**
> It should require some configuration so that it protects you properly.
eg:services running that should be allowed, icmp packets to be accepted, DHCP,etc
Personally i like GUFW best...

is there a guide somewhere for optimal desktop use?

---

### Post by CharlesA on 2010-09-15
Firestarter is no longer being developed. It is better to use something like ufw or gufw and configure the settings from there.

---

### Post by sisco311 on 2010-09-15
Check out the sticky:
[thread=510812]Ubuntu Security[/thread]
and the community docs:
[uhelp]community/UFW[/uhelp]

---

### Post by bodhi.zazen on 2010-09-16
> **webdevelopment said:**
> i was wondering if firestarter (software firewall) works out of the box or does it need some kind of configuration in order for it to provide protection?

is firestarter even needed with ubuntu?

firestarter seems to work for most, although it is starting to show it's age and it is not the default or preferred tool to configure your firewall.

"out of the box" there are no significant open ports, so there is nothing to firewall, and thus adding firestarter adds little.

[ZeroConfPolicySpec - Ubuntu Wiki]("https://wiki.ubuntu.com/ZeroConfPolicySpec")

---

### Post by cariboo on 2010-09-17
About the only thing Firestarter does out of the box is fill up /var/log/kern.log and /var/log/messages.

---

