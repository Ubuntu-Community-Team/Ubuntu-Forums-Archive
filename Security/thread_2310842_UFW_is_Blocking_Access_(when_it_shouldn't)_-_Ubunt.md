---
title: "UFW is Blocking Access (when it shouldn't) - Ubuntu 14.04.3 LTS"
date: 2016-01-22
forum: Security
---

### Post by mcparty2 on 2016-01-22
Good afternoon,

I have a simple wish to lock down my Ubuntu server (IP: 2.2.2.2) to only allow http access to 3 IP addresses (on different subnets)
However, as soon as I add the first rule to allow from one IP address, the access is blocked.

```

Status: active


To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
Anywhere                   ALLOW  1.1.1.1
22 (v6)                    ALLOW       Anywhere (v6)


```

I can confirm my source IP address is correct, the UFW just drops the packet... 

```

Jan 22 14:12:29 nycc-sch-nagios kernel: [186518.192391] [UFW BLOCK] IN=eth0 OUT= MAC=00:0c:29:f2:63:bb:4c:00:82:19:7e:a3:08:00 SRC=1.1.1.1 DST=2.2.2.2 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=1180 DF PROTO=TCP SPT=53890 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 

```

I'm a bit lost. Any assistance would be greatly appreciated. Please find the IPTables rules below which may help:

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            


Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ufw-track-forward  all  --  anywhere             anywhere            


Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            


Chain ufw-after-forward (1 references)
target     prot opt source               destination         


Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-output (1 references)
target     prot opt source               destination         


Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere            


Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            


Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            


Chain ufw-reject-forward (1 references)
target     prot opt source               destination         


Chain ufw-reject-input (1 references)
target     prot opt source               destination         


Chain ufw-reject-output (1 references)
target     prot opt source               destination         


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-track-forward (1 references)
target     prot opt source               destination         


Chain ufw-track-input (1 references)
target     prot opt source               destination         


Chain ufw-track-output (1 references)
target     prot opt source               destination         


Chain ufw-user-forward (1 references)
target     prot opt source               destination         


Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh
ACCEPT     all  --  1.1.1.1         anywhere            


Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         


Chain ufw-user-output (1 references)
target     prot opt source               destination  

```

Sorry about the amount of code - I thought it may pre-empt some questions.

Thank you

---

### Post by mcparty2 on 2016-01-22
This is fixed... this is user error.
Turns out I had the third octet of my IP address wrong.

Replace user... Try again ;)

Thanks to everyone who had a read and a look, sorry to have wasted your time.

---

### Post by QDR06VV9 on 2016-01-22
> [COLOR=#000000]Replace user... Try again [/COLOR]:wink:
Thanks for my **afternoon smile..**:D
Glad you got it sorted!
Cheers

---

