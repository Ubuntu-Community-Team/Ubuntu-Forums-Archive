---
title: "UFW block ICMP when I add a non ICMP related rule"
date: 2011-05-21
forum: Security
---

### Post by MrMonster on 2011-05-21
I am setting up a virtual server. Ubuntu 11.04, "minimal provider image".
UFW was disabled by default. I set it to default deny. Allowed HTTP, SSH and other standard stuff, and enabled it. All seems to be OK. Adding one rule to block some annoying security scanners causes ping not to work. I'm not an Iptables expert, but it looks OK to me. I got it from some website, rather than invented it myself, but modified to to fit the ufw config file syntax. What in that rule prevents pings?!? It seems completely unrelated.

-A ufw-before-input -d <MY-IP> -p tcp --dport 80 -m string --to 70  --algo bm --string 'GET /w00tw00t.at.ISC.SANS.' -j DROP

If I don't add that line, but instead enable ufw without it, and afterward run directly:
iptables -I INPUT -d <MY-IP> -p tcp --dport 80 -m string --to 70  --algo bm --string 'GET /w00tw00t.at.ISC.SANS.' -j DROP
than all is fine.

---

### Post by MrMonster on 2011-05-23
OK, I've worked it out myself. The problem was that there was already a rule:

iptables -I INPUT -d <MY-IP> -p tcp --dport 80 -m string --to 70  --algo bm --string 'GET /w00tw00t.at.ISC.SANS.' -j DROP

stored in Iptables directly when I put the same rule in /etc/ufw/before.rules. It seems that the two cause conflicts, which, for reasons beyond me, prevented ping from working. Manually removing the rule from Iptables and reloading ufw did the trick.

---

