---
title: "Foreign IP address in hosts .allow"
date: 2011-05-30
forum: Security
---

### Post by Peter09 on 2011-05-30
I found this IP address in my hosts.allow

> ALL: 119.42.68.232

Anyone any thoughts on this. I cannot find any other evidence of intrusion.

---

### Post by The Cog on 2011-05-30
That's scary. I looked it up:> inetnum:      119.42.64.0  - 119.42.79.255
netname:      CAT-BB-NET
descr:        10 Fl. 72. CAT TELECOM TOWER Bangrak Bangkok Thailand
I would be inclined to assume the worst. Have you installed any servers? I wonder if **sudo netstat -plantu** shows anything unexpected, or **sudo lsof -i -n -P**, although if you have been got at, then these programs can't really be trusted to tell you the whole truth.
.

---

### Post by Peter09 on 2011-05-31
I'm going to rebuild the server

---

### Post by wlraider70 on 2011-05-31
Hypothetically...
If someone had cracked the server and one of those inputs returns a malicious listening or sending port, What do you do?

---

### Post by Lars Noodén on 2011-05-31
> **wlraider70 said:**
> Hypothetically...
If someone had cracked the server and one of those inputs returns a malicious listening or sending port, What do you do?

You back up the data and do a fresh install of the system.  That is an additional reason to keep programs and data separate: it's easier to back up and restore.

---

