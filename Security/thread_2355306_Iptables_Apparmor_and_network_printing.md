---
title: "Iptables Apparmor and network printing"
date: 2017-03-11
forum: Security
---

### Post by smd3 on 2017-03-11
I'm developing what I hope will be a strict and secure iptables ruleset:

```
## DEFAULT POLICY*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]


## LOGGING / DEBUGGING
-N ACCEPT-LOG
-A ACCEPT-LOG -j LOG --log-level 4 --log-prefix "ACCEPT LOG: "
-A ACCEPT-LOG -j ACCEPT
-N DROP-LOG
-A DROP-LOG -j LOG --log-level 4 --log-prefix "DROP LOG: "
-A DROP-LOG -j DROP


## DROP INVALID INCOMING PACKETS
# INPUT
-A INPUT -m state --state INVALID -j DROP
-A INPUT -p tcp --tcp-flags ALL NONE -j DROP
-A INPUT -p tcp ! --syn -m state --state NEW -j DROP
-A INPUT -p tcp --tcp-flags ALL ALL -j DROP


## INTERNAL INTERFACES
# INPUT
-A INPUT -i lo -j ACCEPT
# OUTPUT
-A OUTPUT -o lo -j ACCEPT


## DNS
# INPUT
-A INPUT -p udp --sport 53 -m state --state ESTABLISHED -j ACCEPT


#OUTPUT
-A OUTPUT -p udp --dport 53 -j ACCEPT


## ICMP
# INPUT
-A INPUT -p icmp --icmp-type 0 -j ACCEPT
-A INPUT -p icmp --icmp-type 3/3 -j ACCEPT
-A INPUT -p icmp --icmp-type 3/4 -j ACCEPT
-A INPUT -p icmp --icmp-type 4 -j ACCEPT
-A INPUT -p icmp --icmp-type 8 -m limit --limit 3/s -j ACCEPT
-A INPUT -p icmp --icmp-type 8 -j LOG --log-prefix "ICMP/IN Excessive: "
-A INPUT -p icmp --icmp-type 8 -j DROP
-A INPUT -p icmp --icmp-type 11 -j ACCEPT
-A INPUT -p icmp --icmp-type 12 -j ACCEPT
-A INPUT -p icmp -m limit -j LOG --log-prefix "ICMP/IN: "


# OUTPUT
-A OUTPUT -p icmp --icmp-type 0 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 3/3 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 3/4 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 4 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 8 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 11 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 12 -j ACCEPT
-A OUTPUT -p icmp -m limit -j LOG --log-prefix "ICMP/OUT: "


## SSH
# INPUT
-A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j LOG --log-prefix "SSH/IN :"
-A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT


# OUTPUT
-A OUTPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT


## HTTP
# INPUT
-A INPUT -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
-A INPUT -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT


# OUTPUT
-A OUTPUT -p tcp --dport 80 -j ACCEPT
-A OUTPUT -p tcp --dport 443 -j ACCEPT


COMMIT



```

Now, I need to figure out how to get printing to my network printer configured.  It's a Brother 2250DN physically connected to my router.

My first thought was that I could look at the log file for a clue as to what was going on, but this is the output to my kern.log:

```
Mar 11 08:07:12 Lemur kernel: [59009.557127] audit: type=1400 audit(1489244832.420:47): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=27321 comm="lpd" capability=12  capname="net_admin"
```

Am I looking in the wrong log, why is apparmor stepping in, and why isn't my logging which I've configured in rules.v4 working?

If I change my default policies to ACCEPT, printing works fine.

---

### Post by Doug S on 2017-03-12
> **smd3 said:**
> Am I looking in the wrong log, why is apparmor stepping in, and why isn't my logging which I've configured in rules.v4 working?I would get logging working first, and then use it to figure out about the printer. From what you have posted, logging isn't working because you never call it. You need last rules before a chain will hit it default policy where you jump to the DROP-LOG user defined chain.

---

### Post by smd3 on 2017-03-13
Thanks, I think I see what you're saying.  The logging event needs to be just before the deny or accept event that I want to log.  I was following some guides, and now that I'm learning more I'm not sure why they would suggest creating a new chain.

I did manage to get printing working, first by changing my printer setup.  I didn't quite know what method the computer was using to print, which made it difficult to determine which ports it was using.  The printer works with PCL6, so I'm using that.  I Google'd for the common ports and added them, now I'll have to start weeding them out one-by-one to determine only the ones I need.

Here's where it stands for now...I'll keep tinkering on that logging. Thanks again!

```
## DEFAULT POLICY*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]


## DROP INVALID INCOMING PACKETS
# INPUT
-A INPUT -m state --state INVALID -j DROP
-A INPUT -p tcp --tcp-flags ALL NONE -j DROP
-A INPUT -p tcp ! --syn -m state --state NEW -j DROP
-A INPUT -p tcp --tcp-flags ALL ALL -j DROP


## INTERNAL INTERFACES
# INPUT
-A INPUT -i lo -j ACCEPT
# OUTPUT
-A OUTPUT -o lo -j ACCEPT


## DNS
# INPUT
-A INPUT -p udp --sport 53 -m state --state ESTABLISHED -j ACCEPT


#OUTPUT
-A OUTPUT -p udp --dport 53 -j ACCEPT


## ICMP
# INPUT
-A INPUT -p icmp --icmp-type 0 -j ACCEPT
-A INPUT -p icmp --icmp-type 3/3 -j ACCEPT
-A INPUT -p icmp --icmp-type 3/4 -j ACCEPT
-A INPUT -p icmp --icmp-type 4 -j ACCEPT
-A INPUT -p icmp --icmp-type 8 -m limit --limit 3/s -j ACCEPT
-A INPUT -p icmp --icmp-type 8 -j LOG --log-prefix "ICMP/IN Excessive: "
-A INPUT -p icmp --icmp-type 8 -j DROP
-A INPUT -p icmp --icmp-type 11 -j ACCEPT
-A INPUT -p icmp --icmp-type 12 -j ACCEPT
-A INPUT -p icmp -m limit -j LOG --log-prefix "ICMP/IN: "


# OUTPUT
-A OUTPUT -p icmp --icmp-type 0 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 3/3 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 3/4 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 4 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 8 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 11 -j ACCEPT
-A OUTPUT -p icmp --icmp-type 12 -j ACCEPT
-A OUTPUT -p icmp -m limit -j LOG --log-prefix "ICMP/OUT: "


## SSH
# INPUT
-A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j LOG --log-prefix "SSH/IN :"
-A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT


# OUTPUT
-A OUTPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT


## HTTP
# INPUT
-A INPUT -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
-A INPUT -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT


# OUTPUT
-A OUTPUT -p tcp --dport 80 -j ACCEPT
-A OUTPUT -p tcp --dport 443 -j ACCEPT


## PRINTING
# INPUT
-A INPUT -p udp --sport 515 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 515 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 54925 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 54925 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 5357 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 5357 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 1900 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 1900 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 9100 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 9100 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 161 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 161 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 162 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 162 -s 192.168.1.140 -j ACCEPT
-A INPUT -p udp --sport 8611 -s 192.168.1.140 -j ACCEPT
-A INPUT -p tcp --sport 8611 -s 192.168.1.140 -j ACCEPT


# OUTPUT
-A OUTPUT -p udp --dport 515 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 515 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 54925 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 54925 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 5357 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 5357 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 1900 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 1900 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 9100 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 9100 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 161 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 161 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 162 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 162 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p udp --dport 8611 -d 192.168.1.140 -j ACCEPT
-A OUTPUT -p tcp --dport 8611 -d 192.168.1.140 -j ACCEPT


COMMIT
```

---

