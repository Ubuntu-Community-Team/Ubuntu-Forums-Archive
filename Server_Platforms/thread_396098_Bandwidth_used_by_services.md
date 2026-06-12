---
title: "Bandwidth used by services"
date: 2007-03-29
forum: Server Platforms
---

### Post by ajoian on 2007-03-29
Hello boys and girls,

I have a little problem, I want to make some "drawings" to see how much traffic is passing via HTTP, FTP, and so on... I know that I have to use mrtg and snmpd/ipfm but how ? Any hints in configuring snmpd will be useful.
P.S: I've read both manuals (mrtg & snmpd) and I don't want to use cacti or ntop.

Best regards,

---

### Post by denver on 2007-03-29
You could use Cacti if you wish to pole your interfaces and/or CPU disk usage so on and so forth. For a complete analisys of traffic originated from one service or another, you could use webalizer.
Both these applications are in the Ubuntu repositories and can be downloaded via apt-get.
Cacti is a RRDtool front end made in PHP ( you need apache to run it )
Webalizer is a log analiser that draws graphs and statistics based on the traffic originated from one of the supported services ( web/FTP/clf/squid ).

Hopes this helps you out a bit. Good Luck!

---

### Post by WesRatcliff on 2007-03-29
Hmm - if you don't want to use Cacti or Ntop (my preference for what you want) then you'll be down to writing some custom SNMP scripts and loading the output into MRTG.

The MRTG docs have some examples of this and your SNMPD server will explain how to run an external script and give it an OID.

Wes

---

