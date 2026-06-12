---
title: "UFW: Translating iptables rule to UFW"
date: 2016-10-20
forum: Security
---

### Post by alakt on 2016-10-20
Hello,

This is the iptables rule:

"-A INPUT -i eth0 -s 10.2.0.51,10.2.0.52 -d 228.0.0.3 -j ACCEPT"

How can i translate it to ufw rule?

Best Regards,

---

### Post by Habitual on 2016-10-20
[https://help.ubuntu.com/community/UFW#Advanced_Syntax](https://help.ubuntu.com/community/UFW#Advanced_Syntax)

---

### Post by alakt on 2016-10-20
> **Habitual said:**
> [https://help.ubuntu.com/community/UFW#Advanced_Syntax](https://help.ubuntu.com/community/UFW#Advanced_Syntax)

I Tried :

root@localhost:~# sudo ufw allow from 10.2.0.51,10.2.0.,52 to 228.0.0.3 to any port
ERROR: Wrong number of arguments

root@localhost:~# sudo ufw allow from 10.2.0.51,10.2.0,52 to 228.0.0.3 to any port proto tcp
ERROR: Wrong number of arguments

What am i missing?

---

### Post by Habitual on 2016-10-20
[https://help.ubuntu.com/community/UFW#Default_rules_are_fine_for_the_average_home_user](https://help.ubuntu.com/community/UFW#Default_rules_are_fine_for_the_average_home_user)
and or [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) in its entirety.

---

### Post by alakt on 2016-10-20
> **Habitual said:**
> [https://help.ubuntu.com/community/UFW#Default_rules_are_fine_for_the_average_home_user](https://help.ubuntu.com/community/UFW#Default_rules_are_fine_for_the_average_home_user)
and or [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) in its entirety.

I underestand that and i read the manual. I still have the syntax wrong..

---

### Post by alakt on 2016-10-21
I figred it out.


That worked for me:


ufw allow to 228.0.0.3 from 10.2.0.51 proto tcp
ufw allow to 228.0.0.3 from 10.2.0.51 proto udp
ufw allow to 228.0.0.3 from 10.2.0.52 proto tcp
ufw allow to 228.0.0.3 from 10.2.0.52 proto udp

---

### Post by Habitual on 2016-10-21
You see where all outgoing connections are allowed by default at that link?
I'm not sure your "rules" are necessary.

---

