---
title: "fail2ban ignore IP -  only first is ignored VERSION 0.8.3-2"
date: 2010-10-25
forum: Server Platforms
---

### Post by mistypotato on 2010-10-25
I saw in the fail2ban change log that in 0.8.2 they fixed a bug where only the first IP was ignored in jail.conf in cases where you had more than one.

In my configuration I have fail2ban 0.8.3-2 which is the current one in the Ubuntu repository and my ignore line is like this.........

ignore = 127.0.0.1 66.249.0.0/24


There is a space between the IP's

Am I doing something wrong or is it still broken ??

---

### Post by mistypotato on 2010-11-04
Place the IP's in the top main part of the config file...NOT...individually in the separate config sections.

---

