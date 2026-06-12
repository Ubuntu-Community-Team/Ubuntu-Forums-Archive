---
title: "No connection between host &amp; guest after 10.04 upgrade"
date: 2010-05-05
forum: Virtualisation
---

### Post by Izmo on 2010-05-05
Configuration is as follows:
Host: Upgraded from 9.10 to 10.04 (Everything worked prior to upgrade.)
Guest: Kubuntu 10.04. Unchanged.
Virtualization: VMware server 2.0.2

After the upgrade I had to reinstall vmware, because of the new kernel. I used Radu Cotescu's script "raducotescu-vmware-server-linux-2.6.3x-kernel-592e882" from here: [http://radu.cotescu.com](http://radu.cotescu.com)

Long story short: Everything works, except I can't contact (not even ping) the guest from the host, or vice versa. Net connection otherwise works fine, both from the guest and the host.

The relevant network stuff...
Host:
```
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:18:8b:30  
          inet addr:192.168.33.210  Bcast:192.168.33.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe18:8b30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:78252114 (78.2 MB)  TX bytes:4937789 (4.9 MB)
          Memory:fe200000-fe220000

vmnet1    Link encap:AMPR NET/ROM  HWaddr   
          inet addr:192.168.232.1  Mask:255.255.255.0
          UP RUNNING  MTU:0  Metric:1
          RX packets:3221225472 errors:0 dropped:0 overruns:0 frame:1470918301
          TX packets:3222651664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:9106480 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:AMPR NET/ROM  HWaddr   
          inet addr:172.16.84.1  Mask:255.255.255.0
          UP RUNNING  MTU:0  Metric:1
          RX packets:4071312384 errors:4071314432 dropped:3847668224 overruns:4071319552 frame:3400371200
          TX packets:4071312994 errors:4071314944 dropped:4071315968 overruns:4071321600 carrier:3400384512
          collisions:4071316992 txqueuelen:0 
          RX bytes:4071313408 (4.0 GB)  TX bytes:4071313920 (4.0 GB)

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.84.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.33.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.232.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.33.254  0.0.0.0         UG    0      0        0 eth0

```

Guest - Here I can't copy/paste because the f&@#%!! connection doesn't work, but I'll type in the most relevant stuff:
```
eth0     ...
         inet addr:172.16.84.128 Bcast: 172.16.84.255 Mask: 255.255.255.0
         ...

Routing table
Destination     Gateway        Genmask       Flags Metric Ref Use Iface
172.16.84.0     0.0.0.0        255.255.255.0 U     1      0   0   eth0
169.254.0.0     0.0.0.0        255.255.0.0   U     1000   0   0   eth0
0.0.0.0         172.16.84.2    0.0.0.0       UG    0      0   0   eth0

```

Any ideas would be appreciated. I've been fighting this crap for 2 days now. (BTW, it's not the firewall settings - I've tried "sudo iptables -F" on both ends. No doughnut.)

---

### Post by Izmo on 2010-05-06
Never mind. I "solved" the issue by migrating to virtualbox. (I probably would have used that in the first place anyway, but it worked like s#!+ in 9.10 so I had to use vmware).

---

### Post by iteman on 2010-05-13
I got the same problem with the solution of [http://radu.cotescu.com/2010/01/19/how-to-install-vmware-server-ubuntu-fedora-opensuse/](http://radu.cotescu.com/2010/01/19/how-to-install-vmware-server-ubuntu-fedora-opensuse/).

The problem caused the host to a guest connection (eg. ping, ssh) to be failed via vmnet1 and vmnet8.

Now I have solved the problem using another solution at [http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html) and an additional patch as follows:

```
--- vmware-server.2.0.1_x64-modules-2.6.30.4-fix.patch.org    2009-10-11 05:18:11.000000000 +0900
+++ vmware-server.2.0.1_x64-modules-2.6.30.4-fix.patch    2010-05-13 12:18:53.000000000 +0900
@@ -296,3 +296,13 @@
      -DKBUILD_BASENAME=\"$(DRIVER)\" \
      -Werror -S -o /dev/null -xc $(1) \
      > /dev/null 2>&1; then echo "$(2)"; else echo "$(3)"; fi)
+--- ./vmnet-only/vnetUserListener.c.org    2010-05-13 12:16:20.000000000 +0900
++++ ./vmnet-only/vnetUserListener.c    2010-05-13 12:17:02.000000000 +0900
+@@ -31,6 +31,7 @@
+ #include "driver-config.h" /* must be first */
+ #include <linux/netdevice.h>
+ #include <linux/poll.h>
++#include <linux/sched.h>
+ #include "compat_skbuff.h"
+ #include "compat_wait.h"
+ #include "vnetInt.h"
--- vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh.org    2009-10-11 05:22:35.000000000 +0900
+++ vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh    2010-05-13 15:21:00.000000000 +0900
@@ -20,6 +20,7 @@
     exit 1
 fi
 cd "$MODSOURCEDIR"
+find . -maxdepth 1 -name '*-temp.tar' | xargs -r rm -f
 TARS=`find . -maxdepth 1 -name '*.tar'`
 if [ ! "$TARS" ]; then
     echo "Sorry, no tar files found in $MODSOURCEDIR"
```

---

### Post by kextyn on 2010-05-13
I had the same problem using this guide:
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

vmnet1 on the host would display:
Link encap:AMPR NET/ROM  HWaddr

But after rebuilding with this guide it's working fine: 
[http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/](http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/)

I also used that risesecurity guide on a fresh install and hostonly was working immediately.

---

