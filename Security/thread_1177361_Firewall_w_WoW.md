---
title: "Firewall w/ WoW"
date: 2009-06-03
forum: Security
---

### Post by Alex Demille on 2009-06-03
Hey all,
Just today there was a new patch for World of Warcraft. now in earlier patches I've managed to DL them fine. This time it's saying my firewall is interfering. Is there a way to access my F.W. and get it to stop blocking the DL?

---

### Post by lovinglinux on 2009-06-03
Ubuntu comes with a firewall, but all traffic is allowed by default. If you didn't installed a firewall manager to modify the built-in firewall rules, then it is most likely that the report is wrong and the problem lies somewhere else.

You might want to check [these threads](http://www.google.com/search?q=WoW+patch+download+problem+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

### Post by c9-3Rr0r on 2009-06-03
I assuming that you are using ufw firewall so just type,
sudo ufw allow #port_number 
From that what blizzard FAQ says you should open ports: 6112, 3724, and 6881


Also if you connect via router forward those ports to your machine

---

