---
title: "Interface connection issue"
date: 2012-03-13
forum: Server Platforms
---

### Post by Jay89 on 2012-03-13
Hello,
   I have an Ubuntu 11.10 64bit email server (a virtual machine hosted on a windows server 2008 computer using Hyper-V) configured so far with dovecot and postfix. I noticed that all of a sudden I was no longer able to send mail to an external destination (lets say google).

I'm just in the testing and configuration phases of the mail setup now but the config for dovecot and postfix look like they are alright.

Next, I looked at the routing table and noticed something weird. The default static route that handles all external traffic keeps changing. I will set it to the correct 173.X.X.X address using the route command but then all external traffic fails. Then once I reboot the machine the default route changes back to the local 10.1.0.X address and my connection is restored.

Also, the 173 interface (eth1) doesn't seem to be routing traffic to begin with, I checked the host machine and all of its interfaces are working fine.

I need it to go out the 173.X.X.X because I need a world routable IP address for the email traffic. 

I checked the interfaces and they are configured correctly. The route command I am using is: 

sudo route add -net default netmask 0.0.0.0 gw 173.X.X.X metric 100 dev eth1.

Thank You
Let me know if anyone needs any other info.

---

### Post by mruiz@ic-sa.com on 2012-03-13
> **Jay89 said:**
> Hello,
   I have an Ubuntu 11.10 64bit email server (a virtual machine hosted on a windows server 2008 computer using Hyper-V) configured so far with dovecot and postfix. I noticed that all of a sudden I was no longer able to send mail to an external destination (lets say google).

I'm just in the testing and configuration phases of the mail setup now but the config for dovecot and postfix look like they are alright.

Next, I looked at the routing table and noticed something weird. The default static route that handles all external traffic keeps changing. I will set it to the correct 173.X.X.X address using the route command but then all external traffic fails. Then once I reboot the machine the default route changes back to the local 10.1.0.X address and my connection is restored.

Also, the 173 interface (eth1) doesn't seem to be routing traffic to begin with, I checked the host machine and all of its interfaces are working fine.

I need it to go out the 173.X.X.X because I need a world routable IP address for the email traffic. 

I checked the interfaces and they are configured correctly. The route command I am using is: 

sudo route add -net default netmask 0.0.0.0 gw 173.X.X.X metric 100 dev eth1.

Thank You
Let me know if anyone needs any other info.

Can you ping out?

what do you get when you do an ifconfig?

---

### Post by Jay89 on 2012-03-16
Hi,
  I can ping out if the route is 10.X.X.X.

ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:15:5d:00:fe:0c
          inet addr:10.1.0.X  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::215:5dff:fe00:fe0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:212852 errors:0 dropped:439 overruns:0 frame:0
          TX packets:1331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26257372 (26.2 MB)  TX bytes:261352 (261.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:15:5d:00:fe:0d
          inet addr:173.X.X.X  Bcast:0.0.0.0  Mask:255.255.255.240
          inet6 addr: fe80::215:5dff:fe00:fe0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211413 errors:0 dropped:439 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26179429 (26.1 MB)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3029 (3.0 KB)  TX bytes:3029 (3.0 KB)

---

