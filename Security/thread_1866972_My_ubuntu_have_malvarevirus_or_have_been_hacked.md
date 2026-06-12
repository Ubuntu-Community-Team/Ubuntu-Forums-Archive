---
title: "My ubuntu have malvare/virus or have been hacked"
date: 2011-10-22
forum: Security
---

### Post by manuel85 on 2011-10-22
Hi

I have problem with my ubuntu LTS 10.04.3 server, there is weird UDP traffic  
since I have no experience in security can someone help.

**netstat -nap**
[COLOR="DarkRed"]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      686/smbd        
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1044/sshd       
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1310/master     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      686/smbd        
tcp        0      0 192.168.2.8:22          192.168.1.203:48190     ESTABLISHED 12736/sshd:
tcp6       0      0 :::22                   :::*                    LISTEN      1044/sshd       
udp        0      0 192.168.2.8:137         0.0.0.0:*                           1077/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1077/nmbd       
udp        0      0 192.168.2.8:138         0.0.0.0:*                           1077/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1077/nmbd       
udp        0      0 0.0.0.0:161             0.0.0.0:*                           1325/snmpd[/COLOR]


tcp dum shows lots of UDP traffic
**tcpdump not host 192.168.1.203**    
[COLOR="DarkRed"]tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
13:24:49.600138 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600259 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600268 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600467 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600474 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600701 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600706 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.600903 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601009 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601013 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601206 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601319 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601427 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601431 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601434 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601438 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601441 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601445 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601449 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601454 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601552 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601556 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601559 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601563 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601567 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601570 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601574 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601579 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601679 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601683 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601686 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601690 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601693 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601697 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601701 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601706 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601709 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601815 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601819 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601822 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601826 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601830 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601833 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601837 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601842 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.601845 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14
13:24:49.602295 IP customer.worldstream.nl.www > 192.168.2.8.28960: UDP, length 14[/COLOR]


**rkhunter -c** didn't find enything
this is rkhunter warnings

[COLOR="DarkRed"]Checking the local host...

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]
    Checking if SSH protocol v1 is allowed                   [ Not allowed ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ][/COLOR]  
    
in **/var/log/rkhunter.log** about hidden files    
[COLOR="DarkRed"][13:28:03] Warning: Hidden directory found: /dev/.udev
[13:28:03] Warning: Hidden directory found: /dev/.initramfs[/COLOR]



Lynis:

**lynis -q**
[COLOR="DarkRed"]      - Checking for password protection...                   [ WARNING ]
  - Checking consistency of group files (grpck)...            [ WARNING ]
    - Minimal of 2 responsive nameservers...                  [ WARNING ]
    - Checking Postfix banner...                              [ WARNING ]
    - Checking for unused rules...                            [ WARNING ]
  - Checking SNMP community strings...                        [ WARNING ]
  - Checking for a running NTP daemon or client...            [ WARNING ]      
 [/COLOR]     
      
clamav didn't find anything

---

### Post by haqking on 2011-10-22
it all looks fine to me, the worldstream stuff is your ISP i am presuming.

As for viruses is it is unlikely as Linux currently has no viruses in the wild, though malware can be written for it, it just is not likely.

so you think you have issues due to the UDP traffic ?

are you a gamer ? as 28960 is a common gaming port

---

### Post by manuel85 on 2011-10-22
> **haqking said:**
> it all looks fine to me, the worldstream stuff is your ISP i am presuming.

No. My ISP is from Croatia.

> **haqking said:**
> As for viruses is it is unlikely as Linux currently has no viruses in the wild, though malware can be written for it, it just is not likely.

so you think you have issues due to the UDP traffic ?

are you a gamer ? as 28960 is a common gaming port

This server is uses as **game server** and 28960 is gaming port (Call of duty), but currently there is about 500kB/s from that IP even COD server app is not running.

google gave me this link when I enter 
**customer.worldstream.nl malvare**

[http://www.malwaredomainlist.com/mdl.php?search=49981&colsearch=All&quantity=50]("http://www.malwaredomainlist.com/mdl.php?search=49981&colsearch=All&quantity=50")

---

### Post by haqking on 2011-10-22
> **manuel85 said:**
> No. My ISP is from Croatia.



This server is uses as **game server** and 28960 is gaming port (Call of duty), but currently there is about 500kB/s from that IP even COD server app is not running.

google gave me this link when I enter 
**customer.worldstream.nl malvare**

[http://www.malwaredomainlist.com/mdl.php?search=49981&colsearch=All&quantity=50]("http://www.malwaredomainlist.com/mdl.php?search=49981&colsearch=All&quantity=50")

have you used cracks etc for your games ?

---

### Post by manuel85 on 2011-10-22
no cracks, this is linux version of COD and it is downloaded from

[http://www.shacknews.com/file/24176/call-of-duty-4-linux-dedicated-server]("http://www.shacknews.com/file/24176/call-of-duty-4-linux-dedicated-server")

---

### Post by manuel85 on 2011-10-22
also I notice today

**ping customer.worldstream.nl**

[COLOR="DarkRed"]Pinging customer.worldstream.nl [127.0.0.1] with 32 bytes of data:
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128[/COLOR]

---

### Post by Dangertux on 2011-10-22
> **manuel85 said:**
> also I notice today

**ping customer.worldstream.nl**

[COLOR=DarkRed]Pinging customer.worldstream.nl [127.0.0.1] with 32 bytes of data:
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128[/COLOR]

It would appear customer.worldstream.nl has a very strange DNS record :-|

```

Non-authoritative answer:
Name:    customer.worldstream.nl
Address: 127.0.0.1

```

Also -- If you're running a COD server, and seeing UDP traffic on its default port that's not odd. Now -- if you are NOT running a COD server then I would be concerned.

None of what you posted looks particularly like anything odd from the situation you've described.

The only thing that is slightly bizarre is the worldstream.nl stuff, however honestly, they are a hosting company. It's not inconceivable something you're doing needs to communicate with their servers.

Just my thoughts.

---

### Post by manuel85 on 2011-10-23
> **Dangertux said:**
> Also -- If you're running a COD server, and seeing UDP traffic on its default port that's not odd. Now -- if you are NOT running a COD server then I would be concerned.


Here is update from yesterday.
Yesterday I add this rule to my iptables:

[B]iptables -A INPUT -s 109.236.83.130 -j DROP                                                                                         
iptables -A OUTPUT -p tcp -d 109.236.83.130 -j DROP[/B]

to block all incoming/outgoing traffic to **109.236.83.130**
this morning **tcpdump -nn not host 192.168.1.203**

[COLOR="DarkRed"]11:22:18.046627 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046629 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046632 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046635 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046638 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046729 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046732 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.046735 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047544 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047549 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047552 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047555 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047557 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047560 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047562 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047565 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047569 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047572 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047574 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047577 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047580 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047583 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047585 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047588 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047591 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047593 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047596 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047600 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047603 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047606 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047608 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047611 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047613 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047616 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047619 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047621 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047624 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047626 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047629 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047632 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047634 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047637 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047639 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047643 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047646 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047649 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047651 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047654 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14
11:22:18.047656 IP 109.236.83.130.80 > 192.168.2.8.28960: UDP, length 14[/COLOR]

UDP traffic is now about 50kB/s and is only one way and there is no one playing on server (0 players)

maybe I'm too paranoid and this is not malware/virus, just someone from WorldStream trying to hack COD server.

thanx for help

---

### Post by kosc on 2011-10-24
try few days not to start game server and see if there is still incoming UDP traffic.

---

### Post by manuel85 on 2011-10-24
> **kosc said:**
> try few days not to start game server and see if there is still incoming UDP traffic.

currently 2 days CoD application have not been and there is still around 200kB/s incoming UDP traffic to "nonstarted" game port (28960UDP).

damn! that's DoS :)

---

