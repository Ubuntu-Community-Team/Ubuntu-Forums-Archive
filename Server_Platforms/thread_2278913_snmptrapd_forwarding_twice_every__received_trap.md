---
title: "snmptrapd forwarding twice every  received trap"
date: 2015-05-19
forum: Server Platforms
---

### Post by arturo15 on 2015-05-19
[FONT=arial]I am running 14.04 server  and am I trying to log traps received from an external source

at the same time I need to forward these traps to another server.

External Source -----> Ubuntu 14.04 ------------>Second server



I works  usign snmptrapd,

[/FONT]NET-SNMP Version:  5.7.2
Web:               [http://www.net-snmp.org/](http://www.net-snmp.org/)
Email:             [EMAIL="net-snmp-coders@lists.sourceforge.net"]net-snmp-coders@lists.sourceforge.net[/EMAIL]
[FONT=arial]

however,  every received trap is re-sent twice from the Ubuntu server  

[/FONT][FONT=arial]External Source ---1x--> Ubuntu 14.04 -----2x----->Second server
[/FONT][FONT=arial]

I have confirmed this with  a sniffer on both the ubuntu server and  the external server

My config in the  snmptrapd.conf file is this:
[/FONT]
authCommunity log,net community1
forward default  201.103.60.138
format2 %V\n%Date:%h:%j:%k-%l/%m/%y\n%v\n--------------\n

I have tried several tweeks but this seems to be a bug

The debuging shows also this behaviour

snmptrapd: Running trap specific handlers
snmptrapd:lookup: Looking up Trap OID: deviceComesOnline
snmptrapd:lookup: get_traphandler exact match (0x16a0bb0)
snmptrapd:auth: Comparing auth types: result=40, request=32, result=1
snmptrapd: forward_handler (201.103.60.138)
snmptrapd:auth: Comparing auth types: result=40, request=32, result=1
snmptrapd: forward_handler (201.103.60.138)
snmptrapd: Running global handlers
snmptrapd:auth: Comparing auth types: result=40, request=8, result=1
snmptrapd: notification_handler


Any idea or help is welcomed

Thanks

---

### Post by david-ribeiro76 on 2015-09-17
Hi arturo15,

I have the same problem on my Ubuntu 10.04.4 and the second snmptrapd see the Trap SNMP from the first snmptrapd server and not from the real equipment which have send the trap :/
I don't know if i have mismatch a configuration but forwarding trap for me is useless...

David

---

