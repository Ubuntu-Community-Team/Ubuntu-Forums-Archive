---
title: "*real time* snmp bandwidth monitoring tool?"
date: 2007-12-10
forum: Server Platforms
---

### Post by edmicman on 2007-12-10
Is there anything out there that will do actual *real time* snmp monitoring?  We've just come off of a Windows demo of PRTG, which works awesome.

I've looked for a free suitable alternative, and everywhere points to MRTG or Cacti or some variation of those.  I've tried both of those in VMs, as well as OpenNMS (which is cool, btw), but frankly, for what I want to do they all stink.  MRTG and Cacti were both extreme hassles to set up, and don't come close to real time monitoring.  All I found were hacks to try and approximate "real time" but still was clumsy at best.  

Is there anything else out there?  I just want to monitor ports on switches and routers for real time bandwidth.  Maybe I'm missing a free windows program that runs as a service?  

Thanks for any info!

---

### Post by GigaVolt on 2007-12-10
Hello edmicman,

I use [Net-SNMP]("http://net-snmp.sourceforge.net/"). This tool is cli and no fear for refresh values

---

### Post by craigp84 on 2007-12-11
PRTG sounds a pretty good match for your interpretation of your needs, i think anything else will be a compromise of some sorts.

hth,

-c

---

