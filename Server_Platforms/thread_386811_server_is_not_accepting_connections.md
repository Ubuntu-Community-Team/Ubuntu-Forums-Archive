---
title: "server is not accepting connections"
date: 2007-03-17
forum: Server Platforms
---

### Post by chartman on 2007-03-17
I am running a web-server which works perfectly fine locally, i.e on localhost. But if I want to access it from another PC in the same network, nothing happens (not even a time-out). I have found an entry in /var/log/kern.log which appears every time I try to open a web-page from the other PC:

Mar 17 17:36:07 DrFaust kernel: [17188053.052000] Inbound IN=eth1 OUT= MAC=00:00:21:f1:f1:73:00:18:de:d5:4c:7f:08:00 SRC=192.168.1.102 DST=
192.168.1.101 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=21457 DF PROTO=TCP SPT=45385 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0

I get similar messages, when I try to nfs-mount a directory (same here: not response whatsoever on the client side):

Mar 17 18:43:18 DrFaust kernel: [17180197.736000] Inbound IN=eth1 OUT= MAC=00:00:21:f1:f1:73:00:18:de:d5:4c:7f:08:00 SRC=192.168.1.102 DST=
192.168.1.101 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=7983 DF PROTO=TCP SPT=39952 **[COLOR="Red"]DPT=111[/COLOR]** WINDOW=5840 RES=0x00 SYN URGP=0

I got nfs to work the other way round, so I think it has nothing to do with connections or my set-up in general. I suspect some security setting on my main PC. How can I find what is blocking the access? Which process/program writes this error into the kern.log??

---

### Post by gombadi on 2007-03-17
This is caused by the firewall.

Open a terminal and type -
sudo iptables -vnL

That will show you all the rules and how many packets have hit each rule.

You will need to change the firewall on the machine to be able to acces the web server and nfs mounts.

---

### Post by chartman on 2007-03-18
This is it! Stupid me... forgot about the firwall installed a long time ago. Thanks a lot!!

---

