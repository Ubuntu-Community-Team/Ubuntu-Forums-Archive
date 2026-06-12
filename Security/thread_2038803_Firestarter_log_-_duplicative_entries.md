---
title: "Firestarter log - duplicative entries"
date: 2012-08-07
forum: Security
---

### Post by pwolf1 on 2012-08-07
My Firestarter's log is full of such entries (always **TCP, port 56930**)

[I]Time:Aug  7 15:31:55 Direction: Unknown In: ppp0 Out: Port:56930 Source:101.160.209.144 Destination: xxxxxx Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Aug  7 15:31:58 Direction: Unknown In: ppp0 Out: Port:56930 Source:101.160.209.144 Destination:[/I]* xxxxxx *[I] Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Aug  7 15:31:59 Direction: Unknown In: ppp0 Out: Port:56930 Source:2.108.109.166 Destination:[/I]* xxxxxx ** Length:52 TOS:0x00 Protocol:TCP Service:Unknown*

What do these connections mean?

---

### Post by Ms. Daisy on 2012-08-07
I don't use Firestarter (and it hasn't been actively developed in years BTW- most folks recommend using [UFW]("https://help.ubuntu.com/community/UFW") or [iptables]("http://help.ubuntu.com/community/IptablesHowTo") instead of Firestarter), so I can't tell if Firestarter is blocking or allowing those connections. I would assume that it only logs blocked connections, but that's just a guess. 

Since the service says "unknown" we can't know what service is using it.  

You could use ```
watch netstat -anpe
``` to get more details on the connections (if they're active connections not being blocked by Firestarter).

Are you behind a NAT - do you have a router between the computer and the interwebz?

---

