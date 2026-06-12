---
title: "SNMP Help"
date: 2012-11-13
forum: Server Platforms
---

### Post by chadk5utc on 2012-11-13
Hello 
I have 3 linux based routers that offer snmp. The primary is Netopia 3347 the other 2 are Ubiquiti PicoStation M2HP and NanoStationM2. I currently have rsyslog configured to receive data from all these devices how ever the logs from the 2 ubiquiti devices are minimally detailed. Ive been trying to figure out how to get more from them so Im interested in snmp. I have googled for several hours without much success. I have all 3 routers set to send data but I have yet to receive any? I will say that so far I have been unsatisfied with information I have found so far on snmp configuration.

---

### Post by TheMightyGirth on 2012-11-14
Hi chadk5utc,

I have had similar problems finding decent info on snmp that makes sense to me. I always end up back at [MRTG]("http://oss.oetiker.ch/mrtg/") which once configured does seem to produce some nice usage graphs but I never quite manage to get the config how I want it.

AFAIK, setting up snmp on a device does not send data out but rather allows something else to come and grab it.

That said, I have only ever used MRTG to get data from switches and routers never from a linux box so I could be talking out of my hat.

---

### Post by elico on 2012-11-14
SNMP allows targets which meant to send data from the software\router to the server.
It called targets.

Most of SNMP supported devices choice will be pulling and not pushing from the server side.

What are you looking for?
What you have used to be server for targets? they wont come like magic...

Tit's better to use SNMP to pull data from the router by the server by scripts etc.


Regards

---

### Post by Habitual on 2012-11-14
> **chadk5utc said:**
> ...I have all 3 routers set to send data but I have yet to receive any? ...

How did you "set to send" exactly?
[http://www.net-snmp.org/tutorial/tutorial-5/demon/snmpd.html](http://www.net-snmp.org/tutorial/tutorial-5/demon/snmpd.html)

---

### Post by chadk5utc on 2012-11-15
after I read a number of "Howto's" I thought Id try my luck at one and set up as described, as for config on the routers its far simpler that I expected check box to activate the service then fill in the 3 blanks for community and contact info that was it?? the net-snmp/syslog created a new log "net-snmp.log" but remains empty. Honestly Im not sure what I want from snmp as Im not 100% sure what it does or the benefits? The routers are commercial AP's and are remote on my property for the barns/horses and equipment areas. Basically I want as much logged information as possible and as much control of them as possible beyond basic setup and config. these are high power 1 full watt each and they reach extended distances and have on occasion found neighbors "attempting" to use them LoL. MAC filtering and iptables are a wonderful thing.
Thanks for the link Ill be reading it for sure as its far better detailed than what I found.

Chad

---

