---
title: "Suggestions for Network Management Station"
date: 2011-09-20
forum: Server Platforms
---

### Post by spynappels on 2011-09-20
Hi guys,

I'm looking for some suggestions for building a NMS to use to monitor and manage some servers in a lab environment. The servers send SNMP traps and as I want to get some more experience with SNMP, that is what I want to focus on.

There does not seem to be a stand out piece of software, but essentially what I want to do is receive the traps sent, log them and possibly view them in some sort of web frontend.

I'd also like to query the servers for things like memory usage etc and store and graph this data and manage things like log levels and trap data levels using a mib. I know that Nagios can do this graphing etc, but I'd like to work with SNMP for this also.

Can anyone point me at some software to look at?

Thanks guys...

---

### Post by ian dobson on 2011-09-21
Hi,

Maybe have a look at munin or nagios. They're both monitoring/logging programs that support snmp for data collection. 

Regards
Ian Dobson

---

