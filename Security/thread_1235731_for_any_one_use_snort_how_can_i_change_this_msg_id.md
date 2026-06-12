---
title: "for any one use snort how can i change this msg id in base"
date: 2009-08-09
forum: Security
---

### Post by TUDORS on 2009-08-09
dear all 
hw can i change the msg id in base from badtraffic same src/dst ip to land attack

---

### Post by The Tronyx on 2009-08-09
You would need to edit the Snort rule in whichever Snort rule set file that is located in.  You could likely just grep the rules directory for the string and find out what file it exists in pretty easily.

---

