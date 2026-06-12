---
title: "Reduce CPU load from samba"
date: 2010-04-22
forum: Server Platforms
---

### Post by R.Bucky on 2010-04-22
I have an Ubuntu Server 8.04 that is operating fairly high CPU loads - Samba appears the culprit. I have 5 main shares with 17 users. Other packages include Apache (2 Wordpress sites for intranet only), YaCy (minimal indexing 10 pages/minute), and a MySQL business database with no more than 10 concurrent users. This only started in the last 2 weeks - updates are not the culprit. 

Any ideas or suggestions to reduce load?

---

### Post by R.Bucky on 2010-04-22
There was a run away process stalling the machine. It was ethstatus!:lolflag:

---

