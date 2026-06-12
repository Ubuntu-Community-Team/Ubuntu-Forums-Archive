---
title: "ddclient not updating"
date: 2009-12-30
forum: Server Platforms
---

### Post by VaineDragon on 2009-12-30
This my ddclient.conf current and all information is correct

# /etc/ddclient.conf
protocol=dnspark
pid=/var/run/ddclient.pid
ssl=yes
login=xxxxx,
password='xxxxxx'
server=www.dnspark.com
use=web, web=ipdetect.dnspark.com, web-skip='Current Address:'
dragonsden.info,

And when I use 
ddclient -daemon=0 -query

root@dragon-server:~# ddclient -daemon=0 -query
use=if, if=eth0 address is 192.168.1.3
use=if, if=lo address is 127.0.0.1
use=web, web=dnspark address is 76.212.166.131
use=web, web=dyndns address is 76.212.166.131
use=web, web=ipdetect.dnspark.com address is 76.212.166.131

When I attempt to force ddclient to update it get this in the daemon.log I get this same error over and over again.

root@dragon-server:/etc# sudo tail -f /var/log/daemon.log
Dec 30 18:23:37 dragon-server ntpd[8056]: kernel time sync status change 0001
Dec 30 18:24:51 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 18:29:51 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 18:34:52 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 18:39:53 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 18:54:55 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 18:59:56 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 19:04:56 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 19:20:03 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.
Dec 30 19:50:24 dragon-server ddclient[5570]: FAILED:   updating dragonsden.info: nochange: No changes made to the hostname(s). Continual updates with no changes lead to blocked clients.


Any clues as to whats up with ddclient?

---

### Post by shred_eng on 2010-01-01
hi, comparing your ddclient.conf to mine, you have a comma after dragonsden.info not sure if thats right, you use a comma to seperate host names but i dont think it ends in a comma otherwise. also i have server=members.dyndns.org, with comma at end and wildcard=yes dont know exactly what it means but my update works. so maybe these comma's are relevent.

good luck :)

---

