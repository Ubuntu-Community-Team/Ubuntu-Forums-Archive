---
title: "IPsec configuration"
date: 2008-11-03
forum: Security
---

### Post by jkrishnankp on 2008-11-03
Hi,

I am new to ubuntu and before getting familiar with it I am under a situation where I need to implement IPsec (ESP transport between 2 systems).

I was able to set up the SA and SPD using setkey command.Then when I send first message (ESP message) over the SA I am not getting it at the receiving side.

On checking /var/log/syslog the following is the ouput 

racoon: INFO: Reading configuration from "/etc/racoon/racoon.conf"
racoon: INFO: Resize address pool from 0 to 255
racoon: INFO: 127.0.0.1[500] used as isakmp port (fd=8)
racoon: INFO: 127.0.0.1[500] used for NAT-T
racoon: INFO: 131.120.126.139[500] used as isakmp port (fd=9)
racoon: INFO: 131.120.126.139[500] used for NAT-T
racoon: INFO: ::1[500] used as isakmp port (fd=10)
racoon: INFO: fe80::219:b9ff:fee3:7cae%eth0[500] used as isakmp port (fd=11)
kernel: [260485.628546] device eth0 entered promiscuous mode
racoon: INFO: unsupported PF_KEY message REGISTER
kernel: [260507.580544] device eth0 left promiscuous mode
Nov  3 12:12:50 toolserver35 racoon: INFO: unsupported PF_KEY message REGISTER
racoon: ERROR: libipsec failed pfkey check (Invalid SA type)
/USR/SBIN/CRON[19179]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
kernel: [260892.228537] device eth0 entered promiscuous mode
racoon: INFO: unsupported PF_KEY message REGISTER
ERROR: such policy already exists. anyway replace it: 131.120.126.139/32[8264] 151.133.76.117/32[7777] proto=udp dir=out
kernel: [260933.528544] device eth0 left promiscuous mode
kernel: [261042.848583] device eth0 entered promiscuous mode
racoon: INFO: unsupported PF_KEY message REGISTER
kernel: [261106.292795] device eth0 left promiscuous mode
-- MARK --
racoon: INFO: unsupported PF_KEY message REGISTER
racoon: INFO: unsupported PF_KEY message REGISTER
racoon: ERROR: libipsec failed pfkey check (Invalid SA type)


Can someone help me and let me know the configurations that needs a recheck inorder to debug this ?. 

Thanks in Advance
Jay

---

