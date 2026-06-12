---
title: "System use 100%+ CPU"
date: 2012-03-12
forum: Server Platforms
---

### Post by amnovikov on 2012-03-12
Hi.
I have ubuntu 11.04 x64 server with ganglia sensor. Recently (March 10th) system begin to raise cpuusage stat and finally go to 100%(and more, if it can). I don`t know reason and all symtomps.
There are only 2 machine of several with this behaviour, All have about 8-10 "CRON" processes (without any args) in "ps" (yet not cpu intensive). "top" and several other command (ls /etc/cron.d/ , ls, cat, "tabbing") via ssh cause session to hang. 
One similar question is about fuser and 11.10 (cron php5 script), but is not the same case.

One more thing - after reboot one server cannot run gmon (ganglia node sensor) anymore  without any reasonable symptoms(can paste output of gmon -d).
Don`t want to reboot second node and don`t like bad ganglia stats.

If anybody knows this or can advice anything - please help.

---

### Post by amnovikov on 2012-03-12
Half of problem solved. apt-get upgrade fix ganglia, some boot problems etc. Still not know what it was. I had options "auto security updates" enabled. Mb this is the cause of not full auto upgrade.

---

