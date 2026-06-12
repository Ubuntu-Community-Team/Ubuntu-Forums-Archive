---
title: "Connection refused on all ports except 22, 80 and 8080"
date: 2015-10-18
forum: Security
---

### Post by mikul on 2015-10-18
Hello!

I have a really annoying problem and i cant figure out why.
I have been trying to open up ports in my firewall but they seams to still be closed, so after a while i realized its probably not my router but on my end the problem lays.
I did this to check if they where open on my end:
```
nc -zv 127.0.0.1 22 80 8080 1337 55555 21 1024 5900 27960 1055
```
and got this result: 
```
Connection to 127.0.0.1 22 port [tcp/ssh] succeeded!
Connection to 127.0.0.1 80 port [tcp/http] succeeded!
Connection to 127.0.0.1 8080 port [tcp/http-alt] succeeded!
nc: connect to 127.0.0.1 port 1337 (tcp) failed: Connection refused
nc: connect to 127.0.0.1 port 55555 (tcp) failed: Connection refused
nc: connect to 127.0.0.1 port 21 (tcp) failed: Connection refused
nc: connect to 127.0.0.1 port 1024 (tcp) failed: Connection refused
nc: connect to 127.0.0.1 port 5900 (tcp) failed: Connection refused
nc: connect to 127.0.0.1 port 27960 (tcp) failed: Connection refused
nc: connect to 127.0.0.1 port 1055 (tcp) failed: Connection refused
```

And that makes me think its on my end, so I'v tried to allowing the ports in ufw, and even turning ufw off.. I even tried to add ruels in iptables to accept the ports but with no success.. 
Now a bit of a noob when it comes to iptables and firewall so might need a bit of help here.
This is what i get when I list rules in iptables: 
```
$: iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination         
monitorix_IN_8  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:143 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_7  udp  --  0.0.0.0/0            0.0.0.0/0            udp spts:1024:65535 dpt:53 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_6  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:3306 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_5  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:139 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_4  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:110 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_3  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:22 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_2  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:80 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_1  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:21 ctstate NEW,RELATED,ESTABLISHED
monitorix_IN_0  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spts:1024:65535 dpt:25 ctstate NEW,RELATED,ESTABLISHED
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
monitorix_IN_8  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:143 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_7  udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:53 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_6  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:3306 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_5  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:139 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_4  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:110 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_3  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:22 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_2  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:80 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_1  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:21 dpts:1024:65535 ctstate RELATED,ESTABLISHED
monitorix_IN_0  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:25 dpts:1024:65535 ctstate RELATED,ESTABLISHED
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain monitorix_IN_0 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_1 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_2 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_3 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_4 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_5 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_6 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_7 (2 references)
target     prot opt source               destination         

Chain monitorix_IN_8 (2 references)
target     prot opt source               destination         

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
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 27000:27015
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 27015:27030
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 27014:27050
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:4380
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:27015
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:3478
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:4379
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:1337 dpt:1337
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:1337 dpt:1337
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:55555 dpt:55555
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:55555 dpt:55555
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:1337
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1337
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:27960
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:27960

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

I don't understand this. Does anyone have any ideas of what could be wrong? Because I'v never had this problem before. 
Just tell me if you need any additional information.

---

### Post by steeldriver on 2015-10-18
What is the actual issue you are having? Do you have services listening on those ports that have become inaccessible?

---

### Post by mikul on 2015-10-18
I just want to open up ports for example torrent client, ftp server, quake server and so on.
For example I'v have tried to have my quake server up and running on port 27960 but I cant access it. 

Normally when I open up ports they are listed as open if I use a tool like [http://www.canyouseeme.org/](http://www.canyouseeme.org/) but lately they are all listed as closed..
Now I'm not 100% sure because I'm not at home, but I think my ftp server is up and running as well on port 21, but that port also is listed as closed and i get connection refused on that one as well with nc and telnet.

---

