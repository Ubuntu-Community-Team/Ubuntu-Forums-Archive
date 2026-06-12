---
title: "Why isn't ufw enabled by Default for network security at the installation?"
date: 2011-06-07
forum: Security
---

### Post by varunaub on 2011-06-07
The default Firewall ufw is not enabled by default at the time of installation and it has to be enabled by the user.Isn't this a security risk or is the user whether ufw is enabled or not secured from external threats?I am not much knowledgeable about network security But I am trying to understand the Ubuntu mentality behind this default setting.:confused:

---

### Post by mikewhatever on 2011-06-07
It's not enabled, because by default, there is nothing to block. There are no listening services in the default installation.

---

### Post by uRock on 2011-06-07
> **mikewhatever said:**
> it's not enabled, because by default, there is nothing to block. There are no listening services in the default installation.

+1 Your system has no open ports, but it will respond to pings and such. It will be visible to others on the local network, but connection attempts would be dropped.

---

### Post by bodhi.zazen on 2011-06-07
[https://wiki.ubuntu.com/SecurityTeam/FAQ#UFW](https://wiki.ubuntu.com/SecurityTeam/FAQ#UFW)

---

### Post by varunaub on 2011-06-07
@bodhi Thanks for the Link

---

