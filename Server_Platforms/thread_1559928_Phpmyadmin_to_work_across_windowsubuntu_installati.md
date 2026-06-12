---
title: "Phpmyadmin to work across windows/ubuntu installation"
date: 2010-08-24
forum: Server Platforms
---

### Post by sokekoke on 2010-08-24
Hi, I currently have windows and linux installed on their own partitions. I have third drive called &#8220;data&#8221; where all my websites are on. Currently I use xamp on windows and lamp on linux, and they both use my website folder on &#8220;data&#8221;. Now I want to make both systems share the same databases, and I need some help to configure phpmyadmin for this. I want my linux phpmyadmin to get same databases as on windows.

I'm very new to linux, so keep that in mind if you wish to help me :-) Thanks very much.

---

### Post by Ryan Dwyer on 2010-08-24
You need to move /var/lib/mysql to the shared drive then reconfigure the location in MySQL's config.

No guarantee it will work either. You're probably using different MySQL versions between the two operating systems, there could be issues with case sensitivity, and there could be permission issues.

---

### Post by sokekoke on 2010-08-24
> **Ryan Dwyer said:**
> You need to move /var/lib/mysql to the shared drive then reconfigure the location in MySQL's config.

No guarantee it will work either. You're probably using different MySQL versions between the two operating systems, there could be issues with case sensitivity, and there could be permission issues.

Thanks ryan!! =) i will try this. If dosen't work ill probably just move all my work to ubuntu platform. Virtualbox is handling my needed windows applications quite well. Thanks again hehe.

---

