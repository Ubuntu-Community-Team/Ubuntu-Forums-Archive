---
title: "virtual host freezes up"
date: 2009-07-12
forum: Virtualisation
---

### Post by logandzwon on 2009-07-12
I'm having an issue with a virtual host on 9.04 with a 9.04 vhost.

I'm running;
dhcpd
dns
slapd
apache
openvpn


The host sees a kvm process running at 100% utilization.  the vhost is completely unresponsive via vnc and existing ssh sessions lock up.

---

### Post by logandzwon on 2009-07-13
Here is the top report at the time of freezing;

top - 08:10:01 up  8:55,  2 users,  load average: 0.02, 0.01, 0.00
Tasks:  88 total,   1 running,  87 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.1%us,  0.3%sy,  0.1%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    499292k total,   282968k used,   216324k free,    49932k buffers
Swap:  1341388k total,        0k used,  1341388k free,   126472k cached


The only thing out of place on the host machine is that one of the CPUs is at 100% due to a KVM proccess.

---

