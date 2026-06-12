---
title: "Monitor VM"
date: 2017-04-13
forum: Virtualisation
---

### Post by stip128 on 2017-04-13
Hi, 

I am sorry if I am making replication of existing thread.

I am using Ubuntu 16.04.

I have several ubuntu virtual machines, and now I am looking for some software to monitor performance(usage of CPU, memory, state) of VMs. 
I have tried with virtualbox and VBoxManage metrics, but it was not so effective cause only user that make VM can see their metrics, and no other user can see any metric about VM. 

So I am looking for any suggestion, anything. Even from CLI

---

### Post by TheFu on 2017-04-13
I treat VMs like regular machines - this applies to everything, including monitoring.  Lots of method and tools exist for that, usually tied into an alarming system like nagios.  Munin, Cacti, SysUsage, and [20 others]("http://munin-monitoring.org/wiki/MuninCompetition").  I use munin and have all the data centrally placed, so graphs can be generated as needed. This saves CPU - a bunch.

Of course, it is always good to know a few quick tools  [https://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](https://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by stip128 on 2017-04-18
Great thank you for your suggestions. I will try it.

---

