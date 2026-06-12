---
title: "server mysql compromised"
date: 2011-02-16
forum: Security
---

### Post by perfectpol7 on 2011-02-16
My Linux server which is running my company website have been hacked.  Today I saw a number of clients (customers) names with some fun characters  entries on my database (mySql). Access denial on really clients. Please  assist, am running Linux Ubuntu 9 and I dont know where to start  troubleshooting this. let me confession that I am still on the learning  curve on Linux

---

### Post by tgalati4 on 2011-02-16
If you have physical access to the machine, you need to disconnect it from the web (unplug it) and put in the LiveCD (desktop or server addition) it doesn't matter.  You will need to reset the mysql root user password, probably the root login password as well.  You are going to boot into the "Rescue" mode using the LiveCD and then follow the helpful commands that others will guide you through to regain control of your system.

---

