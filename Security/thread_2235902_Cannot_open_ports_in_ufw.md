---
title: "Cannot open ports in ufw"
date: 2014-07-23
forum: Security
---

### Post by bigmonmulgrew on 2014-07-23
Hi guys

I'm trying to setup a Teamspeak server to run on my LAMP webserver

After some testing I'm starting to think my issue is a more general ubuntu issue and nothing to do with teamspeak.

The reason I think this is that using a port checker [www.yougetsignal.com/tools/open-ports/](www.yougetsignal.com/tools/open-ports/) I can't access any of the ports I've opened. 
```
9987/udp                   ALLOW       Anywhere
10011/tcp                  ALLOW       Anywhere
30033/tcp                  ALLOW       Anywhere
2008/tcp                   ALLOW       Anywhere
```

I've checked the port forwarding in my router and it seems ok. I had this running on a windows box and just changed the IP address to my ubuntu test server.

I think this may be a slap in the face moment where I've missed something really basic. I've tried opening other ports, ones that are not related to TS3 but I get the same result

I just don't seem to be able to open any ports regardless of the ufw configuration. What am I missing

---

### Post by TheFu on 2014-07-23
Please post the output from **sudo iptables -L** with "code tags" on the forum.

---

### Post by bigmonmulgrew on 2014-07-23
You may notice I have opened some extra ports while testing

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
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

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

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

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             state INVALID
DROP       all  --  anywhere             anywhere             state INVALID
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
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             state INVALID limit: avg 3/min burst 10
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
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state NEW
ACCEPT     udp  --  anywhere             anywhere             state NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data
ACCEPT     udp  --  anywhere             anywhere             udp dpt:20
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp
ACCEPT     udp  --  anywhere             anywhere             udp dpt:fsp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     udp  --  anywhere             anywhere             udp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:telnet
ACCEPT     udp  --  anywhere             anywhere             udp dpt:23
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     udp  --  anywhere             anywhere             udp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:9987
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:30033
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:2008
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:9987
ACCEPT     udp  --  anywhere             anywhere             udp dpt:9987
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10011
ACCEPT     udp  --  anywhere             anywhere             udp dpt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:30033
ACCEPT     udp  --  anywhere             anywhere             udp dpt:30033
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:41144
ACCEPT     udp  --  anywhere             anywhere             udp dpt:41144
ACCEPT     tcp  --  anywhere             anywhere             multiport dports 2011:2110
ACCEPT     udp  --  anywhere             anywhere             multiport dports 2011:2110

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

---

### Post by TheFu on 2014-07-24
Sorry, don't think I can help much. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) and [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741) may be of help, but I doubt it. 
Here's my netbook iptables:
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere

```
The default has been set to deny via **sudo ufw default deny**
On my servers, generally huge lists of blocked IP addresses are used - about 6600 rules there with a few for fail2ban.

When troubleshooting, I simplify and test until it works or a bug is known.  Over and over - simplify and test. Making something more complex that isn't working usually does not help resolve the problem IME.

---

### Post by untrustytahr on 2014-07-24
> **bigmonmulgrew said:**
> Hi guys

The reason I think this is that using a port checker [www.yougetsignal.com/tools/open-ports/]("http://www.yougetsignal.com/tools/open-ports/") I can't access any of the ports I've opened. 


The port scanner is failing because the only unsolicited packets that you are allowing are local/mult/broadcast.  Why are you trying to match addrtype?
```

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere 

```

---

### Post by bigmonmulgrew on 2014-07-24
Ok I thought it made sense ot do some cleaning up.

As far as firewall configuration goes all I have done is to open the ports as shown here using "ufw allow port"

```

Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
20                         ALLOW       Anywhere
21                         ALLOW       Anywhere
80                         ALLOW       Anywhere
23                         ALLOW       Anywhere
443                        ALLOW       Anywhere
3306                       ALLOW       Anywhere
9987/udp                   ALLOW       Anywhere
10011/tcp                  ALLOW       Anywhere
30033/tcp                  ALLOW       Anywhere
41144/tcp                  ALLOW       Anywhere
2011:2110/udp              ALLOW       Anywhere
22                         ALLOW       Anywhere (v6)
20                         ALLOW       Anywhere (v6)
21                         ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6)
23                         ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)
3306                       ALLOW       Anywhere (v6)
9987/udp                   ALLOW       Anywhere (v6)
10011/tcp                  ALLOW       Anywhere (v6)
30033/tcp                  ALLOW       Anywhere (v6)
41144/tcp                  ALLOW       Anywhere (v6)
2011:2110/udp              ALLOW       Anywhere (v6)

```

SO heres the output without the extrea junk I added.
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
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

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

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

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             state INVALID
DROP       all  --  anywhere             anywhere             state INVALID
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
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             state INVALID limit: avg 3/min burst 10
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
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state NEW
ACCEPT     udp  --  anywhere             anywhere             state NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data
ACCEPT     udp  --  anywhere             anywhere             udp dpt:20
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp
ACCEPT     udp  --  anywhere             anywhere             udp dpt:fsp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     udp  --  anywhere             anywhere             udp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:telnet
ACCEPT     udp  --  anywhere             anywhere             udp dpt:23
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     udp  --  anywhere             anywhere             udp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:9987
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:30033
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:41144
ACCEPT     udp  --  anywhere             anywhere             multiport dports 2011:2110

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

I setup the server fresh on a VPC to try this out. the only firewall configuration I've done is as above via ufw allow. I'm not tring to match addrytpe at all. I didnt set that and I'm not totally clear on what it means, something must have set it for me or its a default.

---

### Post by bigmonmulgrew on 2014-07-27
Small update, I've noticed its not just teamspeak thats being ignored. Everything on WAN is being ignored. Ports are forwarded but still wont respond to WAN

---

### Post by TheFu on 2014-07-27
> **bigmonmulgrew said:**
> Small update, I've noticed its not just teamspeak thats being ignored. Everything on WAN is being ignored. Ports are forwarded but still wont respond to WAN

Sounds like the ISP is protecting you from yourself. Not much we can do to help with that.
Perhaps running a port scan against your public IP is something you need to see which ports are actually open? There are free services that do that for the first few thousand ports - or you can ask a friend to run:
**sudo nmap -sT your-pubic-ip**
then email you the report.

---

### Post by bigmonmulgrew on 2014-07-28
Its not my ISP, I am running a web server on this connection, working fine. I'm running a teamspeak server on Windows, running fine, I can access my own network using my external IP, and I have asked a friend to attempt connection form outside my network cant connect to the new server. I've also used a port scanner, ports not open.

I setup a VPC on Virtual box to test adding the TS3 server to my webserver, and to experiment with setting up Citadel.

The new box with respond to anything on LAN IP but wont respond to anything on a WAN IP

---

### Post by bigmonmulgrew on 2014-07-28
Well problem solved and I'd love to know why this was actually a problem.

I have a ubuntu server running minecraft with the same setup pretty much as the problem server so I started going through the config files looking for differences

This is all I found.

Working
```
# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.199
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	dns-nameservers 192.168.0.1
```

Not Working
```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.199
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1
```

I'd have thought that a misconfigured network would have just not worked rather than only blocking WAN. I'd love to know why this happened but I'm just happy its working now.

---

