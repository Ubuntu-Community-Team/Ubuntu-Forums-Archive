---
title: "Unsure of IPTables rules"
date: 2016-08-15
forum: Server Platforms
---

### Post by andrew89898 on 2016-08-15
Hi, A few months ago I set up a server and I wanted to do it right, so I followed a tutorial which configured IPtables. I have ports 80, 443, 25,22 and 12301 open, but I now need to be able to connect to MySQL on this server remotely. So I tried to add an iptables rule which only accepts connections from my IP. I have ran this command:  ```
[COLOR=#333333][FONT=Consolas]iptables -I INPUT -p tcp -s x.x.x.x --dport 22 -j ACCEPT[/FONT][/COLOR]
``` where x.x.x.x is my IP
But I cannot connect to MySQL as the connection is refused, I think there may be a rule which deny's all connections or something. Also an nmap scan shows the port as closed.

Here is my output of ```
iptables -nL 
```
```
Chain INPUT (policy DROP)target     prot opt source               destination
ACCEPT     udp  --  82.1.157.36          0.0.0.0/0            udp dpt:3306
ACCEPT     tcp  --  82.1.157.36          0.0.0.0/0            tcp dpt:3306
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-track-forward  all  --  0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0


Chain f2b-sshd (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-after-forward (1 references)
target     prot opt source               destination


Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:139
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:445
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:68
ufw-skip-to-policy-input  all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination


Chain ufw-after-output (1 references)
target     prot opt source               destination


Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
DROP       all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            239.255.255.250      udp dpt:1900
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination


Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
DROP       all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-reject-forward (1 references)
target     prot opt source               destination


Chain ufw-reject-input (1 references)
target     prot opt source               destination


Chain ufw-reject-output (1 references)
target     prot opt source               destination


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-track-forward (1 references)
target     prot opt source               destination


Chain ufw-track-input (1 references)
target     prot opt source               destination


Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  82.1.157.36          0.0.0.0/0            tcp dpt:22
ACCEPT     udp  --  82.1.157.36          0.0.0.0/0            udp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:443
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:443


Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination


Chain ufw-user-output (1 references)
target     prot opt source               destination



```
And ```
netstat -tulnp
```
```
Active Internet connections (only servers)Proto Recv-Q Send-Q Local Address           Foreign Address         State                PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN               1128/mysqld
tcp        0      0 127.0.0.1:12301         0.0.0.0:*               LISTEN               787/opendkim
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN               1331/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN               1298/master
tcp6       0      0 :::443                  :::*                    LISTEN               1039/apache2
tcp6       0      0 :::80                   :::*                    LISTEN               1039/apache2
tcp6       0      0 :::22                   :::*                    LISTEN               1331/sshd
tcp6       0      0 :::25                   :::*                    LISTEN               1298/master



```

If you need any more info, please ask.

Thanks!

---

### Post by SeijiSensei on 2016-08-15
By default, the version of MySQL that ships with Ubuntu (and many other distributions) does not permit remote connections.

Locate the "bind address" directive in /etc/mysql/my.cnf which will read
```

bind-address            = 127.0.0.1

```
Put a hash mark ("#") in front of that line and restart MySQL.  Better?

---

### Post by andrew89898 on 2016-08-15
Thanks, I have commented out the bind-address line and changed the permitted hostname in phpmyadmin, now all works fine. I would still like a better understanding of IP Tables, could you tell me what the rules are doing? Thanks.

---

### Post by Vegan on 2016-08-15
are you in a datacenter, might need to open a port there too

---

### Post by SeijiSensei on 2016-08-16
> **andrew89898 said:**
> Thanks, I have commented out the bind-address line and changed the permitted hostname in phpmyadmin, now all works fine. I would still like a better understanding of IP Tables, could you tell me what the rules are doing? Thanks.

I write my own firewalls and don't use UFW, so I can only give you some general observations.  From what I can see, a lot of the rules are designed to log various traffic.  However this block here does a lot of the heavy lifting:
```

ACCEPT     tcp  --  82.1.157.36          0.0.0.0/0            tcp dpt:22
ACCEPT     udp  --  82.1.157.36          0.0.0.0/0            udp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:443
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:443

```
These permit inbound traffic to ports 22, 80, and 443, the SSH, HTTP, and HTTPS services respectively.  (Why there are rules for UDP traffic to these ports totally escapes me, though.  All three are TCP services.)

UFW seems to use a lot of "chains," where packets matching a rule are passed to another ruleset for further processing.  I use a few of those; for instance, passing all inbound SMTP traffic to a set of rules that block known spamming hosts.  But UFW seems to take this to the max making it hard to interpret the rules as displayed.

---

### Post by The Cog on 2016-08-16
```
iptables -nL
```
misses important information - which interfaces the rules apply to. Much better is:
```
iptables -nvL
```
Personally, i prefer to use the following which will also list any NAT rules, prints in a format that's easy to pass back into iptables, and I think is easier to understand You can even addn a -c option and see how many times each rule has been hit:
```
iptables-save
```

---

