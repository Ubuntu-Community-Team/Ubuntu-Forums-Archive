---
title: "iptables and netstat"
date: 2009-02-05
forum: Server Platforms
---

### Post by sparkles on 2009-02-05
up until recently i was using my dsl router and dns server and default gateway for my xp box. under this configuration if a connection was made *in* to my computer (say ftp or vnc) if i ran netstat it would show me the address of who was connected e.g. xxx.isp.com.au.

i have since setup a linux box as dns server and default gateway (using webmin, following [these]("http://ubuntuforums.org/showthread.php?t=926001") instructions) and now if someone connects into my xp box and i run netstat, it shows me the ip address of the gateway instead of the ip address or hostname of the person connected in.

similarly, sometimes if i try to make an active ftp connection to an external ftp server i get an error back that says something like 'sorry i don't want to talk to [public ip address] i want to talk to [private ip adress]'. passive connections work without a problem.

is there something i can change to stop those 2 things from happening?

TIA

---

