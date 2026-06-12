---
title: "Web server and virtual hosting"
date: 2019-06-21
forum: Ubuntu/Debian BASED
---

### Post by erotavlas on 2019-06-21
Hi,
I'm upgrading my old system and comparing ubuntu server 18.04 LTS and zentyal 6.0 (based on ubuntu server 18.04 LTS). I successfully configured Web server with virtual hosting (I can surf them from server system).
My Web server has a static IP address provided by the ISP and I have an  external DNS services that associated that static IP to the  corresponding URL. For ubuntu server I changed the configuration for static IP  
```
/etc/network/interfaces 
```
as described [here]("https://www.howtoforge.com/debian-static-ip-address") while for zentyal server I followed the guide [here]("https://doc.zentyal.org/en/firststeps.html#network-configuration-with-zentyal") (I'm not using virtual interfaces since I use a single SSL certificate for my Web sites).
In order to reach the Web server from Internet what is the best option? Changing the file
```
/etc/hosts
```
by adding the line with static IP and corresponding URL as stated [here]("https://www.howtoforge.com/debian-static-ip-address") or is it better to configure a DNS server as described [here]("https://www.tecmint.com/install-and-configure-web-services-on-zentyal/?") for zentyal?
Thank you

---

### Post by TheFu on 2019-06-21
18.04 doesn't use /etc/network/interfaces to anything networking.
It switched to netplan.

---

### Post by erotavlas on 2019-06-22
> **TheFu said:**
> 18.04 doesn't use /etc/network/interfaces to anything networking.
It switched to netplan.

You are right about ubuntu server. However, zentyal is still using /etc/network/interfaces since if I change the configuration from GUI, it changes this file.
Without regarding the method to modify the configuration files, what is the recommend way to install a Web server? By modifying /etc/hosts or other way?

---

### Post by TheFu on 2019-06-22
/etc/hosts has nothing to do with how other systems connect to your web server.

I clearly know ZERO about zentyal.  Does it use APT as the package manager?  If so, then install and configure it just like on any other Ubuntu system.  [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)  There are lots of different web servers, so which do you want/need?

---

### Post by erotavlas on 2019-06-23
I read [here]("https://help.ubuntu.com/lts/serverguide/network-configuration.html") and [here.]("https://www.swiftstack.com/docs/install/configure_networking.html")
> **TheFu said:**
> /etc/hosts has nothing to do with how other systems connect to your web server.
This is true, but it is considered a best practice to change it to avoid DNS request.

> **TheFu said:**
> 
I clearly know ZERO about zentyal.  Does it use APT as the package manager?  If so, then install and configure it just like on any other Ubuntu system.  [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)  There are lots of different web servers, so which do you want/need?

It is a custom ubuntu server 18.04 LTS. I need to restore an old Web server with virtual hosting and HTTPS. I managed to reinstall and configure all except that the server is not reachable from outside of my network. It uses the same IP address and URL as before and the firewall/routing did not change. There is something missing in the machine that I cannot figure out.

---

### Post by QIII on 2019-06-23
Moved to Ubuntu/Debian BASED.

Zentyal is not a "custom Ubuntu server".  It is a distinct OS based on Ubuntu.

---

### Post by TheFu on 2019-06-23
So, which web server do you need/want?  I know lots about some of the choices, but nothing about others.  Also, the web server needed depends on the underlying webapp, so if you have a webapp expecting nginx, but try to install apache, that's asking for more problems.

---

### Post by Doug S on 2019-06-23
Do you know for certain that packets actually arrive at your server? One way to check is to use tcpdump (or wireshark, if you prefer) and watch the related traffic. Example:

```
doug@DOUG-64:~$ sudo tcpdump -n -tttt -i enp4s0 port 80
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on enp4s0, link-type EN10MB (Ethernet), capture size 262144 bytes
2019-06-23 08:05:27.119044 IP 111.202.100.107.36569 > my-ip.80: Flags [S], seq 1594057549, win 14600, options [mss 1460,sackOK,TS val 1866719266 ecr 0,nop,wscale 8], length 0
2019-06-23 08:05:31.118789 IP 111.202.100.107.36569 > my-ip.80: Flags [S], seq 1594057549, win 14600, options [mss 1460,sackOK,TS val 1866723266 ecr 0,nop,wscale 8], length 0
2019-06-23 08:05:39.119012 IP 111.202.100.107.36569 > my-ip.80: Flags [S], seq 1594057549, win 14600, options [mss 1460,sackOK,TS val 1866731266 ecr 0,nop,wscale 8], length 0
2019-06-23 08:05:55.119111 IP 111.202.100.107.36569 > my-ip.80: Flags [S], seq 1594057549, win 14600, options [mss 1460,sackOK,TS val 1866747266 ecr 0,nop,wscale 8], length 0
```
Maybe not the best example, because 111.202.100.107 is banned (as is all of China), and my system just drops the packets, never sending an ACK. However, the point is, that the packets at least arrive at the server. (traffic is very very light to my site, and I gave up waiting for a better example.)
Note: if you also have outgoing port 80 stuff, you might need an additional filter:
```
sudo tcpdump -n -tttt -i enp4s0 port 80 | grep "my-ip\.80"
```

---

### Post by erotavlas on 2019-06-28
Hi,
I had time to try again. As expect 
```
sudo tcpdump -n -tttt -i eth0 port 80
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
2019-06-28 12:42:21.008986 IP externalIP.54154 > myIP.80: Flags [S], seq 4266973636, win 14000, options [mss 1310,nop,wscale 8,nop,nop,sackOK], length 0
2019-06-28 12:42:21.017012 IP externalIP.53902 > myIP.80: Flags [S], seq 3736589984, win 14000, options [mss 1310,nop,wscale 8,nop,nop,sackOK], length 0
2019-06-28 12:42:21.189114 IP externalIP.54114 > myIP.80: Flags [S], seq 5040217, win 14000, options [mss 1310,nop,wscale 8,nop,nop,sackOK], length 0
```

So the traffic is arriving to the server. 

The port for HTTP traffic is open.
```
nmap myIP

Starting Nmap 7.60 ( https://nmap.org ) at 2019-06-28 12:47 CEST
Nmap scan report for myURL (myIP)
Host is up (0.00011s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
8443/tcp open  https-alt
```

Finally, iptables
```
sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
premodules  all  --  anywhere             anywhere            
DNAT       tcp  --  anywhere             myURL  to:myIP
DNAT       tcp  --  anywhere             myURL tcp dpt:http to:myIP

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
postmodules  all  --  anywhere             anywhere            
SNAT       tcp  --  anywhere             myURL  ctstate DNAT to:myIP
SNAT       tcp  --  anywhere             myURL  tcp dpt:http ctstate DNAT to:myIP

Chain postmodules (1 references)
target     prot opt source               destination         

Chain premodules (1 references)
target     prot opt source               destination 
```

The system can surf Internet and locally the Web servers work well.

---

### Post by Doug S on 2019-06-28
Your iptables NAT rules are somewhat of a surprise. Previously it wasn't obvious to me that your box is also a router. You need to describe your network to us in more detail. Also, we need to see the interfaces specified in your iptables nat chains via the "-v" option. I would suggest, and for example from my system (I don't have any forwarded ports at the moment. i.e. the same box is my router and webserver):

```
doug@DOUG-64:~$ sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 1120143 packets, 127416877 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain INPUT (policy ACCEPT 239794 packets, 18623770 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 299827 packets, 24263691 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 11484 packets, 1440783 bytes)
    pkts      bytes target     prot opt in     out     source               destination
  507365 35607306 SNAT       all  --  *      [COLOR="#FF0000"]enp4s0[/COLOR]  0.0.0.0/0            0.0.0.0/0            to:my-external-ip

```That being said, you can continue with your tcpdump investigation, by continuing to follow the traffic. You already showed that the packets arrive at eth0. So next look at them exiting towards your forwarded computer on whatever interface, looking for a response there. Otherwise move to that computer and continue there.

Your nat rules also use "my-ip" in multiple spots, where for the DNAT it should be some local LAN ip. That doesn't make sense, but I assume is just a result of you hiding the actual IPs.

---

### Post by erotavlas on 2019-07-01
Hi,
I made further test and I'm sure that the problem is on firewall. If I disabled it, I'm able to surf my Web site both with HTTP and HTTPS. Whereas with firewall enabled I can only connect to GUI interface and via SSH.
The nmap command executed from the zentyal server:
```
sudo nmap -sT -O -Pn myURL

Starting Nmap 7.60 ( https://nmap.org ) at 2019-07-01 10:50 CEST
Nmap scan report for myURL (myIP)
Host is up (0.00011s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
443/tcp  open  https
8443/tcp open  https-alt
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.8 - 4.9
Network Distance: 0 hops
```
while the same nmap command executed from a different machine:
```
sudo nmap -sT -O -Pn myURL

Starting Nmap 7.01 ( https://nmap.org ) at 2019-07-01 10:52 CEST
Nmap scan report for myURL (myIP)
Host is up (0.070s latency).
Not shown: 931 filtered ports, 66 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
8443/tcp open  https-alt
Device type: general purpose|WAP|specialized|storage-misc|printer
Running (JUST GUESSING): Linux 3.X|4.X|2.6.X (94%), Asus embedded (90%), Crestron 2-Series (89%), HP embedded (89%), Ubiquiti embedded (88%)
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel cpe:/h:asus:rt-ac66u cpe:/o:crestron:2_series cpe:/h:hp:p2000_g3 cpe:/o:linux:linux_kernel:2.6.32 cpe:/h:ubnt:airmax_nanostation
Aggressive OS guesses: Linux 3.10 - 3.19 (94%), Linux 3.2 - 4.0 (91%), Linux 3.13 (90%), Asus RT-AC66U WAP (90%), Linux 3.10 (90%), Linux 3.11 - 3.12 (90%), Linux 3.18 (90%), Crestron XPanel control system (89%), HP P2000 G3 NAS device (89%), Linux 2.6.32 (88%)
No exact OS matches for host (test conditions non-ideal).
```

Finally, the same nmap command executed from a different machine with zentyal firewall disabled:

```

 sudo nmap -sT -O -Pn myURL
Starting Nmap 7.01 ( https://nmap.org ) at 2019-07-01 10:53 CEST
Nmap scan report for myURL (myIP)
Host is up (0.059s latency).
Not shown: 994 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
53/tcp   open     domain
80/tcp   open     http
135/tcp  filtered msrpc
443/tcp  open     https
8443/tcp open     https-alt
Aggressive OS guesses: Linux 3.10 - 3.19 (95%), Linux 3.18 (93%), Linux 3.2 - 4.0 (93%), Linux 3.13 (92%), Asus RT-AC66U WAP (92%), Linux 3.10 (92%), Linux 3.11 - 3.12 (92%), HP P2000 G3 NAS device (91%), OpenWrt Kamikaze 7.09 (Linux 2.6.22) (90%), Linux 2.6.18 - 2.6.22 (90%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 15 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.56 seconds

```

So the Web server ports (80-443) are not open. I configured port forwarding from the [zentyal firewall GUI]("https://doc.zentyal.org/en/firewall.html#firewall-configuration-with-zentyal") and it seem quite straightforward. I do not see any error. 

```
 sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 6911 packets, 417031 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    7036   424495 premodules  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      29     1740 DNAT       tcp  --  eth0   *       0.0.0.0/0            myIP         tcp dpt:443 to:myIP
      96     5724 DNAT       tcp  --  eth0   *       0.0.0.0/0            myIP         tcp dpt:80 to:myIP

Chain INPUT (policy ACCEPT 338 packets, 20208 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1307 packets, 80122 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1307 packets, 80122 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    1307    80122 postmodules  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 SNAT       tcp  --  *      *       0.0.0.0/0           myIP         tcp dpt:443 ctstate DNAT to:myIP
       0        0 SNAT       tcp  --  *      *       0.0.0.0/0           myIP         tcp dpt:80 ctstate DNAT to:myIP

Chain postmodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain premodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination       
   
```



```

sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
preinput   all  --  anywhere             anywhere            
idrop      all  --  anywhere             anywhere             state INVALID
iaccept    all  --  anywhere             anywhere             state RELATED,ESTABLISHED
inospoof   all  --  anywhere             anywhere            
iexternalmodules  all  --  anywhere             anywhere            
iexternal  all  --  anywhere             anywhere            
inoexternal  all  --  anywhere             anywhere            
imodules   all  --  anywhere             anywhere            
iglobal    all  --  anywhere             anywhere            
iaccept    icmp !f  anywhere             anywhere             icmp echo-request state NEW
iaccept    icmp !f  anywhere             anywhere             icmp echo-reply state NEW
iaccept    icmp !f  anywhere             anywhere             icmp destination-unreachable state NEW
iaccept    icmp !f  anywhere             anywhere             icmp source-quench state NEW
iaccept    icmp !f  anywhere             anywhere             icmp time-exceeded state NEW
iaccept    icmp !f  anywhere             anywhere             icmp parameter-problem state NEW
idrop      all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
preforward  all  --  anywhere             anywhere            
fdrop      all  --  anywhere             anywhere             state INVALID
faccept    all  --  anywhere             anywhere             state RELATED,ESTABLISHED
fnospoof   all  --  anywhere             anywhere            
fredirects  all  --  anywhere             anywhere            
fmodules   all  --  anywhere             anywhere            
ffwdrules  all  --  anywhere             anywhere            
fnoexternal  all  --  anywhere             anywhere            
fdns       all  --  anywhere             anywhere            
fglobal    all  --  anywhere             anywhere            
faccept    icmp !f  anywhere             anywhere             icmp echo-request state NEW
faccept    icmp !f  anywhere             anywhere             icmp echo-reply state NEW
faccept    icmp !f  anywhere             anywhere             icmp destination-unreachable state NEW
faccept    icmp !f  anywhere             anywhere             icmp source-quench state NEW
faccept    icmp !f  anywhere             anywhere             icmp time-exceeded state NEW
faccept    icmp !f  anywhere             anywhere             icmp parameter-problem state NEW
fdrop      all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
preoutput  all  --  anywhere             anywhere            
odrop      all  --  anywhere             anywhere             state INVALID
oaccept    all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ointernal  all  --  anywhere             anywhere            
omodules   all  --  anywhere             anywhere            
oglobal    all  --  anywhere             anywhere            
oaccept    icmp !f  anywhere             anywhere             icmp echo-request state NEW
oaccept    icmp !f  anywhere             anywhere             icmp echo-reply state NEW
oaccept    icmp !f  anywhere             anywhere             icmp destination-unreachable state NEW
oaccept    icmp !f  anywhere             anywhere             icmp source-quench state NEW
oaccept    icmp !f  anywhere             anywhere             icmp time-exceeded state NEW
oaccept    icmp !f  anywhere             anywhere             icmp parameter-problem state NEW
odrop      all  --  anywhere             anywhere            

Chain drop (5 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 50/min burst 10 LOG level debug prefix "zentyal-firewall drop "
DROP       all  --  anywhere             anywhere            

Chain faccept (12 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere             NFQUEUE num 0
ACCEPT     all  --  anywhere             anywhere            

Chain fdns (1 references)
target     prot opt source               destination         
faccept    udp  --  anywhere             one.one.one.one      state NEW udp dpt:domain
faccept    tcp  --  anywhere             one.one.one.one      state NEW tcp dpt:domain

Chain fdrop (4 references)
target     prot opt source               destination         
drop       all  --  anywhere             anywhere            

Chain ffwdrules (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain fglobal (1 references)
target     prot opt source               destination         
faccept    all  --  anywhere             anywhere            

Chain fmodules (1 references)
target     prot opt source               destination         

Chain fnoexternal (1 references)
target     prot opt source               destination         

Chain fnospoof (1 references)
target     prot opt source               destination         
fnospoofmodules  all  --  anywhere             anywhere            
fdrop      all  --  myIPNetwork/24       anywhere            

Chain fnospoofmodules (1 references)
target     prot opt source               destination         

Chain fredirects (1 references)
target     prot opt source               destination         
LOG        tcp  --  anywhere            myURL state NEW tcp dpt:https limit: avg 50/min burst 10 LOG level debug prefix "zentyal-firewall redirect "
faccept    tcp  --  anywhere            myURL state NEW tcp dpt:https
LOG        tcp  --  anywhere            myURL state NEW tcp dpt:http limit: avg 50/min burst 10 LOG level debug prefix "zentyal-firewall redirect "
faccept    tcp  --  anywhere            myURL state NEW tcp dpt:http

Chain ftoexternalonly (0 references)
target     prot opt source               destination         
fdrop      all  --  anywhere             anywhere            

Chain iaccept (34 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere             NFQUEUE num 0
ACCEPT     all  --  anywhere             anywhere            

Chain idrop (3 references)
target     prot opt source               destination         
drop       all  --  anywhere             anywhere            

Chain iexternal (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
iaccept    tcp  --  anywhere             anywhere             tcp dpt:ssh state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:https state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:http state NEW
drop       tcp  --  anywhere             anywhere             tcp dpt:5900 state NEW
drop       tcp  --  anywhere             anywhere             tcp dpt:6900 state NEW

Chain iexternalmodules (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain iglobal (1 references)
target     prot opt source               destination         
iaccept    udp  --  anywhere             anywhere             udp dpt:kerberos state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:kerberos state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:loc-srv state NEW
iaccept    udp  --  anywhere             anywhere             udp dpt:netbios-ns state NEW
iaccept    udp  --  anywhere             anywhere             udp dpt:netbios-dgm state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn state NEW
iaccept    udp  --  anywhere             anywhere             udp dpt:ldap state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:ldap state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds state NEW
iaccept    udp  --  anywhere             anywhere             udp dpt:kpasswd state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:kpasswd state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:ldaps state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:3268 state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:3269 state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpts:49152:65535 state NEW
iaccept    udp  --  anywhere             anywhere             udp dpt:ntp state NEW
iaccept    udp  --  anywhere             anywhere             udp dpt:domain state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:domain state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:5900 state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:6900 state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:ssh state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:8443 state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:ftp-data state NEW
iaccept    tcp  --  anywhere             anywhere             tcp dpt:ftp state NEW

Chain imodules (1 references)
target     prot opt source               destination         

Chain inoexternal (1 references)
target     prot opt source               destination         

Chain inointernal (0 references)
target     prot opt source               destination         

Chain inospoof (1 references)
target     prot opt source               destination         
inospoofmodules  all  --  anywhere             anywhere            
idrop      all  --  myIPNetwork/24       anywhere            

Chain inospoofmodules (1 references)
target     prot opt source               destination         

Chain log (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 50/min burst 10 LOG level debug prefix "zentyal-firewall log "
RETURN     all  --  anywhere             anywhere            

Chain oaccept (11 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain odrop (2 references)
target     prot opt source               destination         
drop       all  --  anywhere             anywhere            

Chain oglobal (1 references)
target     prot opt source               destination         
oaccept    all  --  anywhere             anywhere             state NEW

Chain ointernal (1 references)
target     prot opt source               destination         
oaccept    udp  --  anywhere             one.one.one.one      state NEW udp dpt:domain
oaccept    tcp  --  anywhere             one.one.one.one      state NEW tcp dpt:domain

Chain omodules (1 references)
target     prot opt source               destination         
oaccept    tcp  --  anywhere             anywhere             tcp dpt:http

Chain preforward (1 references)
target     prot opt source               destination         

Chain preinput (1 references)
target     prot opt source               destination         

Chain preoutput (1 references)
target     prot opt source               destination    

```

P.S. I'm sorry if I did not explain some detail clearly. My system has one interface eth0, has one fixed IP address provided by the ISP and zentyal 6.0 provides integrated firewall, SSH, GUI and FTP services. Those services SSH, GUI and FTP work well with both firewall enabled and disabled while custom service as apache2 Web server works only with firewall disabled. I think that there is something strange on zentyal GUI configuration that I'm missing.

---

### Post by Doug S on 2019-07-01
> **erotavlas said:**
> 
So the Web server ports (80-443) are not open. I configured port forwarding from the [zentyal firewall GUI]("https://doc.zentyal.org/en/firewall.html#firewall-configuration-with-zentyal") and it seem quite straightforward. I do not see any error.So based on the below part, it seems your box is not a router. Then why are you doing port forwarding? As a test flush the nat tables, but leave the rest:

```
sudo iptables -t nat -F
```

> **erotavlas said:**
> I'm sorry if I did not explain some detail clearly. My system has one interface eth0, has one fixed IP address provided by the ISP and zentyal 6.0 provides integrated firewall, SSH, GUI and FTP services. Those services SSH, GUI and FTP work well with both firewall enabled and disabled while custom service as apache2 Web server works only with firewall disabled. I think that there is something strange on zentyal GUI configuration that I'm missing.Oh!! Thanks for clarifying.

EDIT 1: for whatever reason, you seem to want to keep your public IP address hidden. Then you should edit your previous post and delete the domain name.
EDIT 2: Myself, I find the command "sudo iptables -L" to be useless. Consider to replace that listing with the output from "sudo iptables -v -x -n -L". Machine generated iptables rule sets are extremely difficult to follow, and the packets counters help to trace flow.

---

### Post by erotavlas on 2019-07-01
> **Doug S said:**
> So based on the below part, it seems your box is not a router. Then why are you doing port forwarding? As a test flush the nat tables, but leave the rest:

Of course, it is not a router. The router is directly connect to it. Zentyal has integrated firewall

Then after flushing.
> **Doug S said:**
> 
```
sudo iptables -t nat -F
```

EDIT 2: Myself, I find the command "sudo iptables -L" to be useless. Consider to replace that listing with the output from "sudo iptables -v -x -n -L". Machine generated iptables rule sets are extremely difficult to follow, and the packets counters help to trace flow.

```
sudo iptables -v -x -n -L
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    4497  1418343 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    1498    94830 preinput   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 idrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
    1488    94434 iaccept    all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
      10      396 inospoof   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      10      396 iexternalmodules  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      10      396 iexternal  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      10      396 inoexternal  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      10      396 imodules   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      10      396 iglobal    all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       1       36 iaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 state NEW
       0        0 iaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 0 state NEW
       0        0 iaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3 state NEW
       0        0 iaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4 state NEW
       0        0 iaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11 state NEW
       0        0 iaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12 state NEW
       8      320 idrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 preforward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fdrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
       0        0 faccept    all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 fnospoof   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fredirects  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fmodules   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ffwdrules  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fnoexternal  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fdns       all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fglobal    all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 faccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 state NEW
       0        0 faccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 0 state NEW
       0        0 faccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3 state NEW
       0        0 faccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4 state NEW
       0        0 faccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11 state NEW
       0        0 faccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12 state NEW
       0        0 fdrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    4497  1418343 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    2564   658601 preoutput  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 odrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
    2562   658445 oaccept    all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       2      156 ointernal  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       2      156 omodules   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       2      156 oglobal    all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 oaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 state NEW
       0        0 oaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 0 state NEW
       0        0 oaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3 state NEW
       0        0 oaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4 state NEW
       0        0 oaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11 state NEW
       0        0 oaccept    icmp !f  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12 state NEW
       0        0 odrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain drop (5 references)
    pkts      bytes target     prot opt in     out     source               destination         
       8      320 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 50/min burst 10 LOG flags 0 level 7 prefix "zentyal-firewall drop "
       8      320 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain faccept (10 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 NFQUEUE    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0            NFQUEUE num 0
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain fdns (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 faccept    udp  --  *      *       0.0.0.0/0            1.1.1.1              state NEW udp dpt:53
       0        0 faccept    tcp  --  *      *       0.0.0.0/0            1.1.1.1              state NEW tcp dpt:53

Chain fdrop (4 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 drop       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ffwdrules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 RETURN     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           

Chain fglobal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 faccept    all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain fmodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain fnoexternal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain fnospoof (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 fnospoofmodules  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 fdrop      all  --  !eth0  *       myNetworkIP/24       0.0.0.0/0           

Chain fnospoofmodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain fredirects (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ftoexternalonly (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 fdrop      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain iaccept (34 references)
    pkts      bytes target     prot opt in     out     source               destination         
    1490    94510 NFQUEUE    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0            NFQUEUE num 0
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain idrop (3 references)
    pkts      bytes target     prot opt in     out     source               destination         
       8      320 drop       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain iexternal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      10      396 RETURN     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 state NEW
       0        0 drop       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5900 state NEW
       0        0 drop       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6900 state NEW

Chain iexternalmodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      10      396 RETURN     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           

Chain iglobal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:88 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:88 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:135 state NEW
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137 state NEW
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139 state NEW
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:389 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:389 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445 state NEW
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:464 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:464 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:636 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3268 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3269 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpts:49152:65535 state NEW
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:123 state NEW
       0        0 iaccept    udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:53 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5900 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6900 state NEW
       1       40 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8443 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:20 state NEW
       0        0 iaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:21 state NEW

Chain imodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain inoexternal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain inointernal (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain inospoof (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      10      396 inospoofmodules  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 idrop      all  --  !eth0  *       myNetworkIP/24       0.0.0.0/0           

Chain inospoofmodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain log (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 50/min burst 10 LOG flags 0 level 7 prefix "zentyal-firewall log "
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain oaccept (11 references)
    pkts      bytes target     prot opt in     out     source               destination         
    2564   658601 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain odrop (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 drop       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain oglobal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       2      156 oaccept    all  --  *      *       0.0.0.0/0            0.0.0.0/0            state NEW

Chain ointernal (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 oaccept    udp  --  *      *       0.0.0.0/0            1.1.1.1              state NEW udp dpt:53
       0        0 oaccept    tcp  --  *      *       0.0.0.0/0            1.1.1.1              state NEW tcp dpt:53

Chain omodules (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 oaccept    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80

Chain preforward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain preinput (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain preoutput (1 references)
    pkts      bytes target     prot opt in     out     source               destination 

```

P.S. As you can see, I deleted the two forwarding rules.

---

### Post by Doug S on 2019-07-01
Gee, and I thought UFW generated iptables rules were hard to read and follow.

Anyway, the relevant chain is "iglobal" and it doesn't have port 80 or 443 in its list, so no it won't work. You'll have to add them to the list.
By the way, the "iglobal" allows a bunch of stuff that, in my opinion, it shouldn't.

EDIT: The other possibility is the "iexternal" chain, which does have port 80 and 443, but for whatever reason the first rule is "RETURN" for eth0. You could just delete that rule.

```
sudo iptables -t iexternal --delete 1
```

---

### Post by erotavlas on 2019-07-03
Hi,
I solved, but the solutions is very strange. I have to change firewall rules on "Filtering rules from internal network to Zentyal" instead "Filtering rules from external network to Zentyal" without any port forwarding [source]("https://doc.zentyal.org/en/firewall.html#firewall-configuration-with-zentyal").
Now, with firewall enabled from an external machine.
```
sudo nmap -sT -O -Pn myURL
Starting Nmap 7.01 ( https://nmap.org ) at 2019-07-03 07:59 CEST
Nmap scan report for myURL (myIP)
Host is up (0.062s latency).
Not shown: 994 filtered ports
PORT     STATE  SERVICE
21/tcp   closed ftp
22/tcp   open   ssh
53/tcp   open   domain
80/tcp   open   http
443/tcp  open   https
5900/tcp closed vnc
Aggressive OS guesses: Linux 3.10 - 3.19 (94%), Linux 3.18 (90%), Linux 3.2 - 4.0 (90%), Linux 3.13 (90%), Asus RT-AC66U WAP (90%), Linux 3.10 (89%), Linux 3.11 - 3.12 (89%), Crestron XPanel control system (88%), HP P2000 G3 NAS device (88%), OpenWrt Kamikaze 7.09 (Linux 2.6.22) (87%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.63 seconds
```

Thank you for your support.

---

