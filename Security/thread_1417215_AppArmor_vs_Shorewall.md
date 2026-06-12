---
title: "AppArmor vs Shorewall"
date: 2010-02-27
forum: Security
---

### Post by waloshin on 2010-02-27
For Ubuntu Server 9.10 with :

Apache2, mysql and php5 installed?

Which one would be better AppArmor or Shorewall?

---

### Post by Agent ME on 2010-02-27
They both do different things. Shorewall helps you manage your firewall (who can connect to you), and AppArmor helps limit the damage exploits can do.

---

### Post by rookcifer on 2010-02-27
Yeah they are completely different.  You can't compare them because they aren't meant to do the same thing at all.  Therefore, this Poll = FAIL

---

### Post by bodhi.zazen on 2010-02-27
> **waloshin said:**
> For Ubuntu Server 9.10 with :

Apache2, mysql and php5 installed?

Which one would be better AppArmor or Shorewall?

For a server I would advise you simply learn iptables. It is no more difficult to learn then shorewall.

I would use shorewall for a router or gateway.

In terms of apparmor vs shorewall, a better questions is what is you are expecting these tools to do for you ?

---

