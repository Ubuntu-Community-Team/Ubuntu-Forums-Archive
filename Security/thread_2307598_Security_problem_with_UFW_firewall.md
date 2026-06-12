---
title: "Security problem with UFW firewall"
date: 2015-12-26
forum: Security
---

### Post by mac4 on 2015-12-26
I am running version 14.04.03 desktop Ubuntu and my firewall settings where changed on 2 of my desktop Ubuntu's. On the first the UFW firewall was disabled. when I performed a sudo ufw status it showed disabled.

Both Desktops use openssh server for authentication and are not accessed physically through the console.

The second the UFW firewall entries where changed to include port 631 as follows.

Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
1723/tcp                   ALLOW       Anywhere
631                        ALLOW       Anywhere *

Does anyone have an explanation for the change or recommendation for how this could occur?

---

### Post by ian-weisser on 2015-12-26
Port 631 is usually bound by CUPS, the printing system. Did somebody, perhaps, enable printer sharing or install CUPS?

---

