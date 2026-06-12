---
title: "syslog report shows iptables denied messages for hosts not in drop list ???"
date: 2016-04-10
forum: Security
---

### Post by itsup on 2016-04-10
Here the source ip that is not in the iptables drop list but syslog shows denied.  Access to granted to this host. Is this a configuration issue or bug ?

```
Apr 11 07:45:30 yyyyy kernel: [52607.115254] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC=z.z.z.z
DST=x.x.x.x LEN=104 TOS=0x00 PREC=0x00 TTL=114 ID=5 DF PROTO=TCP SPT=52484 DPT=22 WINDOW=257 RES=0x00 ACK PSH URGP=0
Apr 11 07:45:30 yyyyy kernel: [52607.198795] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC= z.z.z.z DST=x.x.x.x LEN=104 TOS=0x00 PREC=0x00 TTL=115 ID=6 DF PROTO=TCP SPT=52484 DPT=22 WINDOW=257 RES=0x00 ACK PSH URGP=0
Apr 11 07:45:34 yyyyy kernel: [52611.453872] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC= SRC= z.z.z.z DST=x.x.x.x LEN=200 TOS=0x00 PREC=0x00 TTL=115 ID=27 DF PROTO=TCP SPT=52484 DPT=22 WINDOW=258 RES=0x00 ACK PSH URGP=0
Apr 11 07:46:11 yyyyy kernel: [52648.179635] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC= z.z.z.z DST=x.x.x.x LEN=136 TOS=0x00 PREC=0x00 TTL=114 ID=41 DF PROTO=TCP SPT=52484 DPT=22 WINDOW=258 RES=0x00 ACK PSH URGP=0
Apr 11 07:46:11 yyyyy kernel: [52648.265546] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC= z.z.z.z DST=x.x.x.x LEN=120 TOS=0x00 PREC=0x00 TTL=115 ID=42 DF PROTO=TCP SPT=52484 DPT=22 WINDOW=258 RES=0x00 ACK PSH URGP=0
Apr 11 07:46:11 yyyyy kernel: [52648.356122] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC= z.z.z.z DST=x.x.x.x LEN=120 TOS=0x00 PREC=0x00 TTL=115 ID=43 DF PROTO=TCP SPT=52484 DPT=22 WINDOW=257 RES=0x00 ACK PSH URGP=0 
```

Here is src ip that is in the iptables drop list and shows dropped

 ```
Apr 11 07:40:37 garage2 kernel: [52314.098900] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC=183.3.202.114 DST=192.168.1.113 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=1072 DF PROTO=TCP SPT=10926 DPT=22 WINDOW=29200 RES=0x00 SYN URGP=0 
Apr 11 07:40:38 garage2 kernel: [52315.097138] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC=183.3.202.114 DST=192.168.1.113 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=1073 DF PROTO=TCP SPT=10926 DPT=22 WINDOW=29200 RES=0x00 SYN URGP=0 
Apr 11 07:40:40 garage2 kernel: [52317.103694] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC=183.3.202.114 DST=192.168.1.113 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=1074 DF PROTO=TCP SPT=10926 DPT=22 WINDOW=29200 RES=0x00 SYN URGP=0 
Apr 11 07:40:42 garage2 kernel: [52319.206878] iptables denied: IN=eno1 OUT= MAC=00:1e:c9:b7:db:c5:00:1f:e6:37:9c:f0:08:00 SRC=183.3.202.114 DST=192.168.1.113 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=42849 DF PROTO=TCP SPT=49759 DPT=22 WINDOW=29200 RES=0x00 SYN URGP=0
```

---

### Post by Doug S on 2016-04-14
We can not answer without seeing your entire iptables rule set. Well, with 99% certainty, I'll say it is not a bug and it is a configuration issue. Please post the output for "sudo iptables -v -x -n -L".

---

### Post by SeijiSensei on 2016-04-14
Looks like port 22 is blocked which is a good idea in general.  You should only allow SSH connections from IP addresses you trust and only use shared keys.

---

