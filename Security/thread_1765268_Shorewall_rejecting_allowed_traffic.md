---
title: "Shorewall rejecting allowed traffic"
date: 2011-05-22
forum: Security
---

### Post by RyanRahl on 2011-05-22
I have the Shorewall firewall running on Ubuntu 10.10 server and the issue I am having is the firewall is blocking traffic from my transmission-daemon even though I have allowed it in the /etc/shorewall/rules.

the rules file has the following lines
```
ACCEPT		$FW		net	tcp	60000:60035	
ACCEPT		net		$FW	tcp	60000:60035
ACCEPT		$FW		net	udp	51413	
ACCEPT		net		$FW	udp	51413
```

That match the rules in /etc/transmission-daemon/settings.json

```
"peer-port": 51413,
"peer-port-random-high": 60035,
"peer-port-random-low": 60000,
```

yet my syslog gives me this:

```
May 22 18:15:46 sleppery kernel: [ 4374.583353] Shorewall:net2fw:DROP:IN=eth1 OUT= MAC=00:30:48:71:1d:1f:00:22:2d:c9:d4:fb:08:00 SRC=129.241.75.171 DST=74.94.*.* LEN=60 TOS=0x00 PREC=0x20 TTL=48 ID=57853 DF PROTO=TCP SPT=58320 DPT=51413 WINDOW=11680 RES=0x00 SYN URGP=0 
May 22 18:15:47 sleppery kernel: [ 4375.596589] Shorewall:fw2net:REJECT:IN= OUT=eth1 SRC=74.94.*.* DST=94.236.155.247 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=17176 LEN=75 
May 22 18:15:47 sleppery kernel: [ 4375.596704] Shorewall:fw2net:REJECT:IN= OUT=eth1 SRC=74.94.*.* DST=68.14.72.15 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=47712 LEN=75 
May 22 18:15:47 sleppery kernel: [ 4375.596778] Shorewall:fw2net:REJECT:IN= OUT=eth1 SRC=74.94.*.* DST=149.7.96.246 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=1063 LEN=75 
May 22 18:15:47 sleppery kernel: [ 4375.646765] Shorewall:net2fw:DROP:IN=eth1 OUT= MAC=00:30:48:71:1d:1f:00:22:2d:c9:d4:fb:08:00 SRC=188.40.51.2 DST=74.94.*.* LEN=60 TOS=0x00 PREC=0x20 TTL=47 ID=19185 DF PROTO=TCP SPT=43218 DPT=51413 WINDOW=5840 RES=0x00 SYN URGP=0 
```

as you can see, Shorewall is rejecting packets with source and destination port 51413 on incoming net2fw and outgoing fw2net even though the rules are set to accept. any ideas or suggestions?

---

