---
title: "KVM and network problems"
date: 2010-02-25
forum: Server Platforms
---

### Post by RRJ on 2010-02-25
Hello everyone.
I run KVM on 9.10 host and guest 9.10.
both are x64

There is a problem, when i halt the guest os:
my host os looses its connection with internet for 10-15 seconds and then it comes back on. probably something goes wrong with default gateway, as it looses only external network (i still can reach it on my internal network).
I've googled a lot, but cant find anything about that.
i use bridged network.
Could someone please help? i can give any info about my system that you need. (not root of course)

---

### Post by RRJ on 2010-02-25
UPDT:
actually all networks go down. cant reach host pc wih ssh, vnc and nx too.
did anyone face the same problem?
here goes the situation again:
1. i boot up pc, kvm starts and runs perfect.
2. i connect to the host via vnc/nx (trying both)
3. i run virt-manager and boot up the guest os
4. i halt the guest os via its virtual display in virt-manager
5. network on the host pc is down right after the guest shuts down for 10-15 seconds.

its aint normal.. is it?

---

### Post by RRJ on 2010-02-25
anyone?

---

### Post by RRJ on 2010-02-25
still no ideas?

---

### Post by RRJ on 2010-02-26
ok, thank You for Your time and help.
the problemm was in hardware. integrated  
Embedded NC326i Dual Port Gigabit Server Adapter
didnt work right. replaced with other intel card and now it ok.
so if any1 will face such a problem, replace it or wait for new drivers.
btw, if some1 interested - you can make a bugreport.

---

