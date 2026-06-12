---
title: "VMWare/Ubuntu 10.04 : add vCpus ?"
date: 2010-10-15
forum: Server Platforms
---

### Post by bartol_78 on 2010-10-15
Hello everybody,

I've got 2 Ubuntu Servers running as VMs on VMWare ESX 3.5 and they now reach 100% CPU load.

One VMs is configured with one vCpu
The other is configured with two vCpus.

They both run Ubuntu 10.04, Nagios and Cacti.
The kernels are SMP :
 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linu

I realized it's impossible to add more MHz to these machines unless I add more vCpus to them (the server is a 8 cores x2,333Ghz).

So I was wondering if it was easy to add vCPUs to these machines (I have 4 vCpus left) ?

I was thinking :
- 1st machine : 1 vCpu to 2 vCpus
- 2nd machine : 2 vCpus to 4 vCpus

I know I have to stop the servers, add the vCpus and restart. I was wondering if it would have an impact on the servers, create any problem, or if it's completely transparent and just go faster ?

Maybe someone had a similar experience ?

Thank you for your support !

---

