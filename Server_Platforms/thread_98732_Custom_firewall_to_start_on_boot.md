---
title: "Custom firewall to start on boot"
date: 2005-12-04
forum: Server Platforms
---

### Post by DaMasta on 2005-12-04
I created an iptables firewall script called firewall.sh. It currently resides in /etc/init.d/. Can I just link to that script from /etc/rc*.d/ and it will work? Or do all thos links need to have a start/restart/stop parameter? Thanks.

---

### Post by Koybe on 2005-12-04
It should work. Anyway you can use iptables-save to get your rules on anytime ;-)

---

### Post by heimo on 2005-12-04
[quote=DaMasta]I created an iptables firewall script called firewall.sh. It currently resides in /etc/init.d/. Can I just link to that script from /etc/rc*.d/ and it will work? Or do all thos links need to have a start/restart/stop parameter? Thanks.[/quote]

You can use /etc/init.d/skeleton as a template for your script.

---

### Post by DaMasta on 2005-12-04
Thanks guys.

---

