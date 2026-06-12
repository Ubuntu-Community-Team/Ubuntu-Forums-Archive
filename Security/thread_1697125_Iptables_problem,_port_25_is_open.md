---
title: "Iptables problem, port 25 is open"
date: 2011-02-28
forum: Security
---

### Post by W0153R on 2011-02-28
I've recently installed 10.10 server edition, and I must say it was a pleasant suprise, it's just the way I like it. I use it as a squeezebox-server.
But I've run into a problem with the firewall. I did a portscan, which told me there are more ports open then I've told UFW to open. Among which port 25 and 119, when I telnet from another PC to those ports, the connection gets accepted, although there is no answer to any commands (as expected, there's no mail server running).
Iptables print-outs also don't mention anything about the respective ports or a daemon that could be responsable, and the same applies to "ps -e" or "ps aux".

Iptables seems to be working, when I remove the rules to allow samba to work, I can't reach the shares, and when I insert them again I can reach the shares.
"sudo ufw deny from any" as last rule doesn't change anything either (deny incoming is default (although I never issued the command "ufw status verbose" says it is) so it shouldn't, but ports 25 and 119 shouldn't be open either).

---

### Post by brian_p on 2011-02-28
> **W0153R said:**
> 

But I've run into a problem with the firewall. I did a portscan, which told me there are more ports open then I've told UFW to open. Among which port 25 and 119, when I telnet from another PC to those ports, the connection gets accepted, although there is no answer to any commands (as expected, there's no mail server running).


This is expessed in a rather confusing way. An open port is one which has a service running on it. No service, no open port, no accepted connection.

Port 25 is likely a mail server; exim4 possibly.

What does

```
telnet IP_number_of_machine 25
```

say?

---

### Post by W0153R on 2011-02-28
That's why I posted, I don't get it, there's no mail server running.

Just to be clear, my workstation runs Windows 7.
When I telnet the ubuntu box on port 25, it briefly says it's making a connection and immediatly goes to a blank screen with a blinking cursor, entering commands like helo moves the cursor but doesn't add any text.

Here's my "ps aux" print-out:
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   2860  1592 ?        Ss   18:01   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    18:01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    18:01   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    18:01   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    18:01   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    18:01   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    18:01   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    18:01   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    18:01   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    18:01   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    18:01   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    18:01   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    18:01   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    18:01   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    18:01   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    18:01   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    18:01   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    18:01   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    18:01   0:00 [ata_aux]
root        20  0.0  0.0      0     0 ?        S    18:01   0:00 [ata_sff/0]
root        21  0.0  0.0      0     0 ?        S    18:01   0:00 [khubd]
root        22  0.0  0.0      0     0 ?        S    18:01   0:00 [kseriod]
root        23  0.0  0.0      0     0 ?        S    18:01   0:00 [kmmcd]
root        25  0.0  0.0      0     0 ?        S    18:01   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S    18:01   0:00 [kswapd0]
root        27  0.0  0.0      0     0 ?        SN   18:01   0:00 [ksmd]
root        28  0.0  0.0      0     0 ?        S    18:01   0:00 [aio/0]
root        29  0.0  0.0      0     0 ?        S    18:01   0:00 [ecryptfs-kthrea]
root        30  0.0  0.0      0     0 ?        S    18:01   0:00 [crypto/0]
root        37  0.0  0.0      0     0 ?        S    18:01   0:00 [kstriped]
root        38  0.0  0.0      0     0 ?        S    18:01   0:00 [kmpathd/0]
root        39  0.0  0.0      0     0 ?        S    18:01   0:00 [kmpath_handlerd]
root        40  0.0  0.0      0     0 ?        S    18:01   0:00 [ksnapd]
root        41  0.2  0.0      0     0 ?        S    18:01   0:22 [kondemand/0]
root        42  0.0  0.0      0     0 ?        S    18:01   0:00 [kconservative/0]
root       185  0.0  0.0      0     0 ?        S    18:01   0:00 [scsi_eh_0]
root       186  0.0  0.0      0     0 ?        S    18:01   0:00 [scsi_eh_1]
root       203  0.0  0.0      0     0 ?        S    18:01   0:00 [jbd2/sda1-8]
root       204  0.0  0.0      0     0 ?        S    18:01   0:00 [ext4-dio-unwrit]
root       266  0.0  0.1   2388   604 ?        S    18:01   0:00 upstart-udev-bridge --daemon
root       268  0.0  0.1   2356   724 ?        S<s  18:01   0:00 udevd --daemon
root       354  0.0  0.1   2324   568 ?        S<   18:01   0:00 udevd --daemon
root       355  0.0  0.1   2324   568 ?        S<   18:01   0:00 udevd --daemon
syslog     514  0.0  0.2  33712  1264 ?        Sl   18:01   0:00 rsyslogd -c4
root       600  0.0  0.1   1852   544 tty4     Ss+  18:01   0:00 /sbin/getty -8 38400 tty4
root       604  0.0  0.1   1852   552 tty5     Ss+  18:01   0:00 /sbin/getty -8 38400 tty5
root       610  0.0  0.1   1852   548 tty2     Ss+  18:01   0:00 /sbin/getty -8 38400 tty2
root       612  0.0  0.1   1852   548 tty3     Ss+  18:01   0:00 /sbin/getty -8 38400 tty3
root       616  0.0  0.1   1852   552 tty6     Ss+  18:01   0:00 /sbin/getty -8 38400 tty6
root       620  0.0  0.1   2456   760 ?        Ss   18:01   0:00 cron
daemon     622  0.0  0.0   2312   356 ?        Ss   18:01   0:00 atd
wouter     669  0.0  2.4  67296 12448 ?        Sl   18:01   0:01 /home/wouter/MusicIP/MusicMagicServer start
104        706  0.0  0.2   2984  1320 ?        S    18:01   0:00 /bin/bash /usr/sbin/squeezeboxserver_safe /usr/sbin/squeezeboxserver --prefsdir /var/lib/squeezeboxserver/prefs --logdir /var/log/squeezeboxserver/ --cachedir /var/lib/squeezeboxserver/cache --charset=utf8
mysql      709  0.3  3.5 155576 17696 ?        Ssl  18:01   0:29 /usr/sbin/mysqld
104        723  0.5 17.7  94348 88652 ?        S    18:01   0:43 /usr/bin/perl -w /usr/sbin/squeezeboxserver --prefsdir /var/lib/squeezeboxserver/prefs --logdir /var/log/squeezeboxserver/ --cachedir /var/lib/squeezeboxserver/cache --charset=utf8
root       732  0.0  0.1   2296   568 ?        Ss   18:01   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root       764  0.0  0.3  13452  1660 ?        Ss   18:01   0:00 /usr/sbin/winbindd
root       771  0.0  0.2  13412  1420 ?        S    18:01   0:00 /usr/sbin/winbindd
root       796  0.0  0.1   5636   960 ?        Ss   18:01   0:00 /usr/sbin/sshd
root       852  0.0  0.3   9332  1588 ?        Ss   18:01   0:00 nmbd -D
104        939  0.5  4.9 124952 24904 ?        Sl   18:01   0:40 /usr/sbin/mysqld --defaults-file=/var/lib/squeezeboxserver/cache/my.cnf
root       958  0.0  0.8  16788  4088 ?        Ss   18:01   0:00 smbd -F
root       960  0.0  0.1   1852   548 tty1     Ss+  18:01   0:00 /sbin/getty -8 38400 tty1
root       963  0.0  0.4  13748  2448 ?        S    18:01   0:00 /usr/sbin/winbindd
root       964  0.0  0.1  13308   956 ?        S    18:01   0:00 /usr/sbin/winbindd
root       966  0.0  0.2  16788  1152 ?        S    18:01   0:00 smbd -F
root      1029  0.0  0.7  17028  3640 ?        S    18:03   0:00 smbd -F
root      1237  0.0  0.0      0     0 ?        S    20:03   0:00 [flush-8:0]
root      1256  0.8  0.5   8220  2548 ?        Ss   20:07   0:00 sshd: wouter [priv]
wouter    1258  0.0  0.2   8220  1092 ?        S    20:07   0:00 sshd: wouter@pts/0
wouter    1259  6.5  1.0   6440  5028 pts/0    Ss   20:07   0:01 -bash
wouter    1288  0.0  0.1   2504   956 pts/0    R+   20:07   0:00 ps aux
```And my "iptables -L":
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

Chain OUTPUT (policy ACCEPT)
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
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
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
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
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
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.10.0/24      anywhere            tcp dpt:ssh 
ACCEPT     udp  --  192.168.10.0/24      anywhere            udp dpt:ssh 
ACCEPT     tcp  --  192.168.10.0/24      anywhere            tcp dpt:10002 
ACCEPT     udp  --  192.168.10.0/24      anywhere            udp dpt:10002 
ACCEPT     tcp  --  192.168.10.0/24      anywhere            tcp dpt:9000 
ACCEPT     udp  --  192.168.10.0/24      anywhere            udp dpt:9000 
ACCEPT     tcp  --  192.168.10.0/24      anywhere            tcp dpt:3483 
ACCEPT     udp  --  192.168.10.0/24      anywhere            udp dpt:3483 
ACCEPT     udp  --  192.168.10.0/24      anywhere            multiport dports netbios-ns,netbios-dgm /* 'dapp_Samba' */ 
ACCEPT     tcp  --  192.168.10.0/24      anywhere            multiport dports netbios-ssn,microsoft-ds /* 'dapp_Samba' */ 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

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

---

