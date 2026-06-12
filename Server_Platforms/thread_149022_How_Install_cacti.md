---
title: "How Install cacti?"
date: 2006-03-23
forum: Server Platforms
---

### Post by Kostyan on 2006-03-23
I make all under the instruction described in [https://wiki.ubuntu.com/CactiHowTo](https://wiki.ubuntu.com/CactiHowTo)
I reach a step " 5. Install Cacti: apt-get install cacti "
And in the answer:
root@ns84-86:/home/oper * apt-get install cacti
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cacti

The file  /etc/apt/sources.list  is left in by default, without additional adjustments.

Can you help me to solve this problem?

---

### Post by Kostyan on 2006-03-23
All appeared easier than I thought:
1. We climb in/etc/apt/sources.list
Uncomment 19,20 line
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
We save.
2. apt-get update
3. apt-get install cacti

---

