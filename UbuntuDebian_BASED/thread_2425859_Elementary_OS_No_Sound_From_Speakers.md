---
title: "Elementary OS No Sound From Speakers"
date: 2019-08-31
forum: Ubuntu/Debian BASED
---

### Post by putnam120 on 2019-08-31
As the title suggest my system is no longer playing sound through the speakers on my laptop (Asus zenbook). This started after I performed an update and rebooted my laptop.

Was wondering if anyone else has had any sound issues and any ideas on how I can fix the issue. I'm willing to provide any additional information that would be useful in solving this problem.

---

### Post by jeremy31 on 2019-08-31
Moved to Ubuntu/Debian based

---

### Post by mk11110000 on 2019-09-03
Same issue is on HP Spectre x360 15" for Ubuntu 18.04.3 LTS. After latest update, HDMI sound started to work. But internal speakers and headphones/mic are not working anymore (even if the HDMI is unplugged before the laptop boots).
Seems to be related with this post [https://askubuntu.com/questions/1168881/rolling-back-linux-5-0-on-18-04-after-installing-hwe](https://askubuntu.com/questions/1168881/rolling-back-linux-5-0-on-18-04-after-installing-hwe)

[FONT=arial]For me this worked to fix it [/FONT][FONT=&quot][FONT=arial](maybe just to reinstall [/FONT][/FONT][FONT=&quot][FONT=arial]linux-generic-hwe-18.04 could resolve it, but I have not tested it[/FONT][/FONT][FONT=&quot][FONT=arial])[/FONT][/FONT][FONT=arial]:[/FONT][FONT=courier new]

sudo apt remove linux-generic-hwe-18.04
sudo apt install linux-generic
poweroff
[/FONT][FONT=&quot]sudo apt remove linux-generic[/FONT][FONT=courier new]
sudo apt install linux-generic-hwe-18.04
poweroff[/FONT]

---

### Post by bashkos on 2020-08-07
Thanks, it helped me

---

