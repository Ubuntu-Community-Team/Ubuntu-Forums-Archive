---
title: "cannot access internet, lan works."
date: 2009-10-16
forum: Server Platforms
---

### Post by maestropu on 2009-10-16
Symptoms: 

I can't access the internet on my server. I have no problems within my LAN. The thing that perplexes me the most is that I have a bunch of virtual machines running with vmware server, and they can access the internet no problem. My machine has an uptime of 42 days, and this problem definitely didn't exist a month ago. Since then, there has been an internet outage that refreshed my IP. Also, my ISP is verizon fios. 

Because the virtual machines can access the internet, I have no problem ssh-ing into a virtual machine and then using the lan to ssh into the server. 

The server has two adapters connected to the same stock verizon router.

```

$ ping google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
^C
--- google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2004ms
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.642 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.593 ms
$ ifconfig
eth0      Link encap:Ethernet  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fefc:e871/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:707839592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:710065758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:844503546613 (844.5 GB)  TX bytes:635547963805 (635.5 GB)
          Memory:fbde0000-fbe00000

eth1      Link encap:Ethernet 
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fefc:e83b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217548556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:565767015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:15368224446 (15.3 GB)  TX bytes:828393313424 (828.3 GB)
          Memory:fbce0000-fbd00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1836988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1836988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:908829653 (908.8 MB)  TX bytes:908829653 (908.8 MB)
$ cat /etc/resolv.conf
search home
nameserver 192.168.1.1


```I'm running 2.6.28-11-server #42-Ubuntu SMP x86_64 GNU/Linux. 

Anyone got any recommendations???

---

### Post by maestropu on 2009-10-16
Actually it worked after I took the second adapter down and back up. I have no idea why this happened, but hooray!

---

### Post by lykwydchykyn on 2009-10-16
Sounds like you lost your default gateway setting for some reason.  You can check this with the "route" command.

---

