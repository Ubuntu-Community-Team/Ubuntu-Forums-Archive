---
title: "starting Navicat"
date: 2008-01-17
forum: Server Platforms
---

### Post by honiball on 2008-01-17
This might be doff question, but...

I installed navitat to the following folder:
   /usr/src/navicat/navicat8_mysql_en

I then type the following:
   sudo ./start_navicat

...and then nothing visible happens.  I get presented with a new command line.

My question: How do I start the navicat GUI on Linux?

Thanks.

Andrew

---

### Post by frankos44 on 2008-02-16
To start navicat8  jusr type ./start_navicat in the extracted folder.

Navicat works fine on 32bit Ubuntu 7.10 but I have had no success with 64bit Ubuntu 7.10

This is due to Navicat actually running in conjunction with wine. I am working on this at the moment but would be pleased to here from anyone who already knows the fix.

---

### Post by frankos44 on 2008-02-16
> **frankos44 said:**
> To start navicat8  jusr type ./start_navicat in the extracted folder.

Navicat works fine on 32bit Ubuntu 7.10 but I have had no success with 64bit Ubuntu 7.10

This is due to Navicat actually running in conjunction with wine. I am working on this at the moment but would be pleased to here from anyone who already knows the fix.

Found the problem. 

I simply deleted the Navicat folder
re-installed wine using the Synaptic Package Manager
Extracted Navicat again
typed ./start_navicat

All is well now

---

