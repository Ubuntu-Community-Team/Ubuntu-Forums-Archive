---
title: "CPU usage for Guest OS's"
date: 2012-05-19
forum: Virtualisation
---

### Post by David Herring on 2012-05-19
What should the cpu usage be for a KVM guest OS (windows 2003 in this case), when the guest is idle. 

I  have three windows guests configured on a Ubuntu 11.10 host...and top  will always give them each as using ~15% cpu. Is this normal ? The  reason I ask is that I want to move to low power servers, and my  understanding with modern hardware is that power consumption is  dramatically less when the machine is idle...but this will never be the  case if it is the host for KVM virtual machines. (A second question will  be can anyone recommend a low powered server for running KVM virtual  machines ?)

Top output below,

Thanks Dave

top - 07:50:21 up 2 days, 22:00,  3 users,  load average: 0.05, 0.03, 0.05
Tasks: 145 total,   1 running, 144 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.3%us,  4.5%sy,  0.0%ni, 93.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16465144k total,  9822684k used,  6642460k free,   155932k buffers
Swap: 16777212k total,    18884k used, 16758328k free,  5254796k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 2447 libvirt-  20   0 4321m 4.0g 4344 S   17 25.7 838:39.53 kvm                
 7853 libvirt-  20   0 4309m 4.0g 5044 S   16 25.6 244:33.50 kvm                
 8445 libvirt-  20   0 4309m 4.0g 5044 S   15 25.6 234:47.76 kvm                
   45 root      20   0     0    0    0 S    0  0.0   0

---

### Post by David Herring on 2012-05-19
I appreciate that the windows 2003 system is never going to be truely idle...but 15% seems a lot when it has no users logged in, and is running no major server processes.

Dave

---

### Post by TheR on 2012-05-20
My 2003 servers are idling somewhere around 8% (3Ghz 4core i7 Xeon). One of the problems looks to be swapping which can't be omitted. The other is as I remember from old posts real time interrupts.

2008 is much better. Mostly idling at less than 2%.


by
TheR

---

### Post by gordintoronto on 2012-05-20
What CPU? Top says your total CPU usage is 6.8%, so that's not so terrible.

---

### Post by David Herring on 2012-05-21
Thanks for the answers .. yes top does have ~6% for what I believe is total cpu usage (all cores combined ?). But each virtual windows 2003 machine is using ~15% of their allocated cpu resource (2 cores allocated to each...have 8 cores on system in total). 

But the key point is windows 2003 does not play as friendly when running idle as other more modern OS's. I put a ubuntu 12.04 guest on the system, and as you can see below it's cpu usage is effectively 0 when idle.

Thx again for letting me know this is normal cpu usage for a windows 2003 guest,
Dave



top - 07:39:15 up 4 days, 21:48,  3 users,  load average: 0.00, 0.03, 0.05
Tasks: 144 total,   2 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.9%us,  3.5%sy,  0.0%ni, 94.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16465144k total, 14626500k used,  1838644k free,   308168k buffers
Swap: 16777212k total,    27028k used, 16750184k free,  7694124k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
21535 libvirt-  20   0 4310m 4.0g 5084 S   17 25.6 394:20.55 kvm                
15374 libvirt-  20   0 4321m 4.0g 5088 S   16 25.7 507:02.50 kvm                
21583 libvirt-  20   0 4311m 4.0g 5080 R   16 25.6 410:15.19 kvm                
27395 libvirt-  20   0 2251m 1.9g 4556 S    1 12.4  39:14.35 kvm                
 6511 dave      20   0 21468 1368  980 R    0  0.0   0:00.86 top                
    1 root      20   0 24172 2012 1272 S    0  0.0   0:01.33 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root

---

