---
title: "Can't graph disk io &amp; memory in virt-manager"
date: 2010-10-06
forum: Server Platforms
---

### Post by pawzlion on 2010-10-06
I installed the latest 10.04.1 server minimal install and enabled the virtualisation option. I compiled enough X so that I could run virt-manager and I was able to create a couple of VMs and run them and manage them, but the problem is that in the graphs in manager, I can only get CPU usage, not Disk or Network IO. The options are greyed out.

Am I missing something required for these graphs to work ? If so, what please ?

---

### Post by candlerb on 2010-10-21
I get the same with 10.04 desktop (not compiling anything from source - even under server, I would have thought that "apt-get install virt-manager" would have pulled in all its dependencies automatically)

I found the solution here:
[http://www.techotopia.com/index.php/Managing_and_Monitoring_CentOS_based_KVM_Guest_Systems#Monitoring_Virtual_Machine_Performance](http://www.techotopia.com/index.php/Managing_and_Monitoring_CentOS_based_KVM_Guest_Systems#Monitoring_Virtual_Machine_Performance)

Basically you just have to turn on stats collection under Edit>Preferences.

HTH,

Brian.

---

