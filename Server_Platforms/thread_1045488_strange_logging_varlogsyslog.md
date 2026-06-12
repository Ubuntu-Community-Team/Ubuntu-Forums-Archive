---
title: "strange logging /var/log/syslog"
date: 2009-01-20
forum: Server Platforms
---

### Post by denni on 2009-01-20
Get this in my syslog constantly 

tail -f /var/log/syslog brings this stream of data

> Jan 20 19:33:47 ns1 kernel: [  111.020449] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=66.230.160.1 LEN=45 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=26187 LEN=25
Jan 20 19:33:48 ns1 named[8494]: client 66.230.128.15#39904: query (cache) './NS/IN' denied
Jan 20 19:33:48 ns1 kernel: [  111.993165] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=66.230.128.15 DST=192.168.1.5 LEN=45 TOS=0x00 PREC=0x00 TTL=46 ID=6491 PROTO=UDP SPT=39904 DPT=53 LEN=25
Jan 20 19:33:48 ns1 kernel: [  111.993381] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=66.230.128.15 LEN=45 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=39904 LEN=25
Jan 20 19:33:48 ns1 kernel: [  112.120497] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=66.230.128.15 DST=192.168.1.5 LEN=73 TOS=0x00 PREC=0x00 TTL=55 ID=45683 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.1.5 DST=66.230.128.15 LEN=45 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=UDPSPT=53 DPT=39904 LEN=25 ]
Jan 20 19:33:48 ns1 named[8494]: client 66.230.160.1#48154: query (cache) './NS/IN' denied
Jan 20 19:33:48 ns1 kernel: [  112.653081] BANDWIDTH_IN:IN=eth1 OUT= MAC=00:13:d3:e9:a1:d4:00:13:49:3a:45:d7:08:00 SRC=66.230.160.1 DST=192.168.1.5 LEN=45 TOS=0x00 PREC=0x00 TTL=47 ID=42947 PROTO=UDP SPT=48154 DPT=53 LEN=25
Jan 20 19:33:48 ns1 kernel: [  112.653290] BANDWIDTH_OUT:IN= OUT=eth1 SRC=192.168.1.5 DST=66.230.160.1 LEN=45 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=48154 LEN=25


Do anyone know what is going on and what to do to stop this unwanted traffic 

Truly strange behaviour.

---

### Post by mmichalik on 2009-02-03
Denni,

I'm seeing this in my logs as well.  Unfortunately, there isn't a lot of help out there yet about this.  From what I have read so far, it's a DDoS (Distributed Denial of Service) attack.

I've been adding the following line to my iptables.up.rules file in the /etc/ directory.

-A INPUT -s xx.xx.xx.xx -j DROP

where xx.xx.xx.xx is the IP address coming through in the "query (cache) './NS/IN' denied" line.  I've had to add 6 of these lines so far, while I search for a better solution.  I also turned off the ability to ping my server by closing the port the icmp runs on, which is typcially -1.  That slowed down the "query (cache) './NS/IN' denied" lines in my syslog A LOT!

If you don't have IPTABLES running by default when your machine starts up, you can set it up via WEBMIN and apply the changes and they will take effect. (I can't remember the cmd to apply changes to the iptables.up.rules file right now)

Hope that helps.

Mike

---

### Post by jms1989 on 2009-03-18
I'm getting a simular error except its DEST is from another linux box thats downloading the contents from its hdd fro replacement. Because its constantly being recorded, my log files grow so big that they fill the little partition in a matter of a couple days of just copying. Is there a way to excude this type of messages from appearing in my syslog?

---

