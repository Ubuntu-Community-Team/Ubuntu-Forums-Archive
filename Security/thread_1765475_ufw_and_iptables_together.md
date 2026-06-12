---
title: "ufw and iptables together?"
date: 2011-05-23
forum: Security
---

### Post by onehitxzibit on 2011-05-23
Can I have both ufw and iptables running together? My server is currently using ufw, if I add an iptables rule will it have any effect?

---

### Post by Lars Noodén on 2011-05-23
> **onehitxzibit said:**
> Can I have both ufw and iptables running together? My server is currently using ufw, if I add an iptables rule will it have any effect?

There is really only iptables because UFW is a front-end for iptables.  Whichever method you used last will take priority.

---

### Post by onehitxzibit on 2011-05-23
So if I have some ufw rules and then I add an iptables rule it will override the ufw ones? Do I have to enable iptables via command or is it activated all the time?

---

### Post by Lars Noodén on 2011-05-23
> **onehitxzibit said:**
> So if I have some ufw rules and then I add an iptables rule it will override the ufw ones? Do I have to enable iptables via command or is it activated all the time?


If you have rules via UFW and then add ones via iptables directly, then you will have both mixed.

iptables is up and running all the time whether you have set rules for it or not.

---

### Post by sj1410 on 2011-05-23
but when you'll restart UFW, it will overright iptables rules. you can do almost everything from UFW that you need to do with iptables. I recommend using either of them. for more on UFW you can refer

[Ubuntu Uncomplicated Firewall]("http://blog.swapnil.me/2011/04/ubuntu-uncomplicated-firewall.html")

---

### Post by onehitxzibit on 2011-05-23
I need the connection limit future of iptables but I can't get it working. 

If I use 
> iptables -A INPUT -p tcp --syn --dport 22 -m connlimit --connlimit-above 2 -j DROP
it doesn't have any effect, I can still connect as many times as I want. :confused:

EDIT: nvm, I have some rules related to port 22 before this one and they seem to override it. When I put it on top everything's fine. :)

Thank you all for the help!

---

### Post by iX9 on 2011-05-24
Can anyone help me solve this?

How to get incoming connection by teredo (ipv6) adapter in KTorrent?

My ufw settings:
```

ee@aa:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

Do                         Akce        Od
--                         ----        --

6881                       ALLOW IN    Anywhere
6881                       ALLOW IN    Anywhere (v6)

ee@aa:~$

```

KTorrent is listening on 6881 port.
My ufw log is full of this:
> 
May 24 18:19:45 aa kernel: [ 1157.419846] [UFW BLOCK] IN=teredo OUT= MAC= SRC=2001:0000:5ef5:79fd:10b7:103e:a83f:5f09 DST=2001:0000:98aa:064c:14b2:3333:b2cf:77ca LEN=40 TC=0 HOPLIMIT=21 FLOWLBL=0 PROTO=59
May 24 18:19:45 aa kernel: [ 1157.619125] [UFW BLOCK] IN=teredo OUT= MAC= SRC=2001:0000:5ef5:79fd:38e6:3c1a:a54b:3311 DST=2001:0000:98aa:064c:14b2:3333:b2cf:77ca LEN=40 TC=0 HOPLIMIT=21 FLOWLBL=0 PROTO=59
May 24 18:20:05 aa kernel: [ 1177.346269] [UFW BLOCK] IN=teredo OUT= MAC= SRC=2001:0000:5ef5:73b8:3884:1735:2baf:b6fd DST=2001:0000:98aa:064c:14b2:3333:b2cf:77ca LEN=40 TC=0 HOPLIMIT=21 FLOWLBL=0 PROTO=59 


How to enable protocol 59 in firewall?
Ufw supports only tcp/udp protocol.
If I have ufw disabled, inc. connection by teredo works - there is a lot of them succesed in KTorent log. But when is ufw enable, no ipv6 incoming connections any more, and ufw's log is full of above....:(

And this is my ip6tables:
```

ee@aa:~$ sudo ip6tables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw6-before-logging-input  all      ::/0                 ::/0                
ufw6-before-input  all      ::/0                 ::/0                
ufw6-after-input  all      ::/0                 ::/0                
ufw6-after-logging-input  all      ::/0                 ::/0                
ufw6-reject-input  all      ::/0                 ::/0                
ufw6-track-input  all      ::/0                 ::/0                

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw6-before-logging-forward  all      ::/0                 ::/0                
ufw6-before-forward  all      ::/0                 ::/0                
ufw6-after-forward  all      ::/0                 ::/0                
ufw6-after-logging-forward  all      ::/0                 ::/0                
ufw6-reject-forward  all      ::/0                 ::/0                

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw6-before-logging-output  all      ::/0                 ::/0                
ufw6-before-output  all      ::/0                 ::/0                
ufw6-after-output  all      ::/0                 ::/0                
ufw6-after-logging-output  all      ::/0                 ::/0                
ufw6-reject-output  all      ::/0                 ::/0                
ufw6-track-output  all      ::/0                 ::/0                

Chain ufw6-after-forward (1 references)
target     prot opt source               destination         

Chain ufw6-after-input (1 references)
target     prot opt source               destination         
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:137 
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:138 
ufw6-skip-to-policy-input  tcp      ::/0                 ::/0                tcp dpt:139 
ufw6-skip-to-policy-input  tcp      ::/0                 ::/0                tcp dpt:445 
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:67 
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:68 

Chain ufw6-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw6-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw6-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw6-after-output (1 references)
target     prot opt source               destination         

Chain ufw6-before-forward (1 references)
target     prot opt source               destination         
DROP       all      ::/0                 ::/0                rt type:0 
ufw6-user-forward  all      ::/0                 ::/0                

Chain ufw6-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all      ::/0                 ::/0                
DROP       all      ::/0                 ::/0                rt type:0 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 135 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 136 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 133 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 134 HL match HL == 255 
ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED 
ACCEPT     icmpv6    fe80::/10            ::/0                ipv6-icmp type 129 
ufw6-logging-deny  all      ::/0                 ::/0                state INVALID 
DROP       all      ::/0                 ::/0                state INVALID 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 1 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 2 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 3 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 4 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 128 
ACCEPT     udp      ::/0                 ::/0                udp spt:67 dpt:68 
ACCEPT     udp      ::/0                 ff02::fb/128        udp dpt:5353 
ufw6-user-input  all      ::/0                 ::/0                

Chain ufw6-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw6-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw6-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw6-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all      ::/0                 ::/0                
DROP       all      ::/0                 ::/0                rt type:0 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 135 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 136 HL match HL == 255 
ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED 
ufw6-user-output  all      ::/0                 ::/0                

Chain ufw6-logging-allow (0 references)
target     prot opt source               destination         
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw6-logging-deny (1 references)
target     prot opt source               destination         
RETURN     all      ::/0                 ::/0                state INVALID limit: avg 3/min burst 10 
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw6-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw6-reject-input (1 references)
target     prot opt source               destination         

Chain ufw6-reject-output (1 references)
target     prot opt source               destination         

Chain ufw6-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all      ::/0                 ::/0                

Chain ufw6-skip-to-policy-input (6 references)
target     prot opt source               destination         
DROP       all      ::/0                 ::/0                

Chain ufw6-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all      ::/0                 ::/0                

Chain ufw6-track-input (1 references)
target     prot opt source               destination         

Chain ufw6-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp      ::/0                 ::/0                state NEW 
ACCEPT     udp      ::/0                 ::/0                state NEW 

Chain ufw6-user-forward (1 references)
target     prot opt source               destination         

Chain ufw6-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp      ::/0                 ::/0                tcp dpt:6881 
ACCEPT     udp      ::/0                 ::/0                udp dpt:6881 

Chain ufw6-user-limit (0 references)
target     prot opt source               destination         

Chain ufw6-user-limit-accept (0 references)
target     prot opt source               destination         

Chain ufw6-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw6-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw6-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw6-user-output (1 references)
target     prot opt source               destination         
ee@aa:~$

```

Any suggestion?

---

