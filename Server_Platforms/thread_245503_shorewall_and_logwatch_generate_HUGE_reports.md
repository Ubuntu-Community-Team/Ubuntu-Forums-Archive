---
title: "shorewall and logwatch generate HUGE reports"
date: 2006-08-27
forum: Server Platforms
---

### Post by Frank-Hamersley on 2006-08-27
Does anyone have experience with Dapper Server and the combination of shorewall and logwatch (v7.1 11/12/05) producing very large email reports?

It seems that shorewall is timestamping the kernal log messages (which look like "[1026207.326003] Shorewall:inet2all:DROP:") and this causes logwatch to raise a report entry for every log line...rather than producing the (normal) heavily summarised report on ports suffering abuse.

Are there any tips on the best way to quieten it down?  Should  shorewall be targeted to change its message format or should logwatch to be desensitised to the part of the message in the []?

Cheers, Frank.

---

### Post by Frank-Hamersley on 2006-09-11
Still wrestling with this ... logwatch extract follows ...

   From 195.49.61.98 - 3 packets
       To 202.173.129.5 - 3 packets
          Service: ssh (tcp/22) ([470495.273177] Shorewall:Limit:DROP:SSH) - 1 packet
          Service: ssh (tcp/22) ([470498.268772] Shorewall:Limit:DROP:SSH) - 1 packet
          Service: ssh (tcp/22) ([470504.283783] Shorewall:Limit:DROP:SSH) - 1 packet

I can't imagine no one else is having this problem, but my googlin' etc has gained no traction at all - is source code the next (and last resort)?

Cheers, Frank.

---

### Post by Frank-Hamersley on 2006-09-20
OK - have gained a bit on this by creating /etc/logwatch/ignore.conf with a single entry "Shorewall".

Now all I am getting is ...

Dropped 9999 packets on interface ppp0
   From 195.49.61.98 - 3 packets
      To 202.173.129.5 - 3 packets
[..]
34333 Ignored lines

I guess this means poking into the perl scripts to get a better outcome!

Cheers, Frank.

---

