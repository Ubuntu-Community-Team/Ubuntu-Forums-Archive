---
title: "Script to monitor network interface card utilization?"
date: 2013-06-03
forum: Server Platforms
---

### Post by termvrl on 2013-06-03
Hi All,

I want to ask, how can i write a script that can check current nic load, for e.g incoming traffic. 
How did we measure (if it use any parameter) the nic load, "heavy" load or "low" load.

Thanks!                 
             
                         
                                                                                                            
     

p/s: i have post this on programming talk, but then think this is related to servers. sorry.

---

### Post by linuxtechguy on 2013-06-03
You can write it however you want.

---

### Post by SeijiSensei on 2013-06-03
A simple solution would be to write a script that uses ifconfig to obtain the interface's traffic figures:

```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 11:11:11:11:11:11
          inet addr:xx.xx.xx.xx  Bcast:xx.xx.xx.255  Mask:255.255.255.0
          inet6 addr: 2600:3c01::f03c:91ff:feae:72e6/64 Scope:Global
          inet6 addr: fe80::f03c:91ff:feae:72e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141489788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134878179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37693719576 (35.1 GiB)  TX bytes:58344459807 (54.3 GiB)
          Interrupt:48 

```

The script would look something like this:

```

#!/bin/bash

COUNTS=$(ifconfig eth0 | grep 'RX bytes')
RX=$(echo $COUNTS | awk '{print $2}' | awk -F: '{print $2}')
TX=$(echo $COUNTS | awk '{print $6}' | awk -F: '{print $2}')

echo "Received: $RX; Transmitted: $TX"

exit 0

```

That would return "Received: 37693719576; Transmitted: 58344459807"

You could run a version of this script nightly from cron and compile the results into a CSV file for later analysis.

---

### Post by jonobr on 2013-06-03
Hello

Using a more network approach, 
Have you looked at using SNMP?
This would allow you to poll devices for information,
You could grab oodles of information so long as SNMP is running.
Theres a bunch of programs out there that would do this for you, eg [MRTG]("http://oss.oetiker.ch/mrtg/").
Again, if you want quick and dirty its not for you, but if you wanted something that would scale then this is a good route

---

### Post by CharlesA on 2013-06-04
Would vnstat work for you? It monitors traffic and gives you a summary, but I do not think it alerts you if there is *too much* traffic.

---

### Post by termvrl on 2013-06-04
Hi All , Thanks for your reply. 
I did the script. Its work. The output :- Received: 841251; Transmitted: 2080150

What i want to do is, 
If the "Received" > 1000000,  Return 1, which indicates the incoming traffic is heavy.
Else, return 0. The incoming traffic is normal.

I will try to modified the script.

Thanks.

---

### Post by Cheesemill on 2013-06-04
To get the current network transfer rate you can use sar (you will need to install the sysstat package).
```
rob@arch:~$ sar -n DEV 1 1
Linux 3.9.4-2-ck (arch)     04/06/13     _x86_64_    (4 CPU)

16:32:28        IFACE   rxpck/s   txpck/s    rxkB/s    txkB/s   rxcmp/s   txcmp/s  rxmcst/s
16:32:29           lo      0.00      0.00      0.00      0.00      0.00      0.00      0.00
16:32:29       enp2s0    101.00    117.00      8.15    116.28      0.00      0.00      0.00

Average:        IFACE   rxpck/s   txpck/s    rxkB/s    txkB/s   rxcmp/s   txcmp/s  rxmcst/s
Average:           lo      0.00      0.00      0.00      0.00      0.00      0.00      0.00
Average:       enp2s0    101.00    117.00      8.15    116.28      0.00      0.00      0.00

```

You can use this with grep and awk if you want to parse a specific value from the output, for example...

Receive...
```
rob@arch:~$ sar -n DEV 1 1 | grep Average | grep enp2s0 | awk '{print $5}'
8.44
```

Transmit...
```
rob@arch:~$ sar -n DEV 1 1 | grep Average | grep enp2s0 | awk '{print $6}'
119.41
```

You'll need to replace enp2s0 with your interface name, probably eth0.

---

