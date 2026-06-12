---
title: "UFW Input Errors"
date: 2011-05-03
forum: Security
---

### Post by w14219 on 2011-05-03
Server: Ubuntu 10.10
Application: Squid/squidGuard
**Issue: Massive Input Errors - Internet Traffic almost stops!!**
LAN: eth1
WAN: eth2
Squid: port 8080
 
**UFW Configuration:**
**File:** /etc/ufw/before.rules
# nat Table rules
*nat
: POSTROUTING ACCEPT [0:0]
# Forward traffic from eth2 through eth0.
-A POSTROUTING -s 172.20.0.0/16 -o eth2 -j MASQUERADE
-A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to- 8080
#iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE
# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT
 
**File: **[FONT=Courier New]/etc/default/ufw[/FONT]
DEFAULT_FORWARD_POLICY="ACCEPT"
 
**File:**[FONT=Courier New]/etc/ufw/sysctl.conf[/FONT]
net/ipv4/ip_forward=1
 
**Story:**
I just implemented this server for the first time and am getting great Proxy content filtering, but the network configuration is having massive errors.
The network provider looked at the router configuration, cisco, and stated that the LAN traffic has a 70% failure. This is causing me great STRESS as it is all coming from my Ubuntu box... 
 
I am not sure how to resolve this.
 
**Need:**
route all LAN through the WAN
filter ports to tighten security
Force all traffic from port 80 through 8080
Allow the use of internet applications, such as skyward and adobe framework (ports 5000-5003)
 
Any assistance would be greatly appreciated.
 
Thanks,
Mike

---

### Post by bodhi.zazen on 2011-05-03
You will need to start by monitoring you network traffic, what is causing the activity ? Use tcpdump, snort, wireshark, etc.

You will next need to learn iptables.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Other then that general advice we would need a bit more detail to provide specific answers. What traffic are you routing through squid ? One machine or several ? What traffic is a problem ? etc etc

---

### Post by w14219 on 2011-05-03
All issues started when users began to login, in the morning.
 
**User Activities:**
google mail
iscorp (citrix based application)
FrameMaker (ports 5000-5003)
 
**What traffic are you routing through squid ?**
Port 8080 web traffic is being ported through Squid. In addition to that, squidGuard is doing a URL rewrite for google, yahoo, bing. (This appends safetysearch = Strict to block adult content.) 
**One machine or several ? **All machines just SLOW down to a crawl
**What traffic is a problem ? **All WAN based applications
**How is the 80 to 8080 redirect done? **-A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to- 8080 (via /etc/ufw/before.rules)
**What happens when UFW is disabled? **The traffice seems to be A LOT better. I went from several hundred input errors in seconds to ~45 input errors in the approx amount of same time.

**UFW logging:**
Below is the copy of BLOCKed content, from this mornings headache.
**XXX.XXX.XXX.XXX**= eth2 , public IP address. I replaces to protect the innocent.
 
[B]sudo vi UFWMay3BLOCK.log
[/B]May  3 09:16:36 squidGuard kernel: [64639.938264] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=209.85.225.83 DST=xxx.xxx.xxxx LEN=1263 TOS=0x00 PREC=0x00 TTL=55 ID=39420 PROTO=TCP SPT=443 DPT=1856 WINDOW=16260 RES=0x00 ACK PSH URGP=0
May  3 09:16:45 squidGuard kernel: [64649.105950] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63006 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.107154] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63007 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.108390] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63008 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.109614] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63009 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.110842] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63010 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.112078] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63011 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.113306] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63012 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.114539] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63013 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.115768] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63014 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.118231] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63015 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.119464] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63016 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.121923] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63017 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:16:45 squidGuard kernel: [64649.125610] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63018 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK PSH FIN URGP=0
May  3 09:16:46 squidGuard kernel: [64649.221610] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=74.125.95.97 DST=xxx.xxx.xxxx LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=10841 PROTO=TCP SPT=443 DPT=1790 WINDOW=11219 RES=0x00 ACK FIN URGP=0
May  3 09:16:46 squidGuard kernel: [64649.929228] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=209.85.225.83 DST=xxx.xxx.xxxx LEN=1263 TOS=0x00 PREC=0x00 TTL=55 ID=39421 PROTO=TCP SPT=443 DPT=1856 WINDOW=16260 RES=0x00 ACK PSH URGP=0
May  3 09:16:55 squidGuard kernel: [64659.201813] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=74.125.95.97 DST=xxx.xxx.xxxx LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=10842 PROTO=TCP SPT=443 DPT=1790 WINDOW=11219 RES=0x00 ACK FIN URGP=0
May  3 09:16:56 squidGuard kernel: [64659.934100] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=209.85.225.83 DST=xxx.xxx.xxxx LEN=1263 TOS=0x00 PREC=0x00 TTL=55 ID=39422 PROTO=TCP SPT=443 DPT=1856 WINDOW=16260 RES=0x00 ACK PSH URGP=0
May  3 09:16:58 squidGuard kernel: [64661.599044] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=199.34.228.106 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=63019 DF PROTO=TCP SPT=80 DPT=50808 WINDOW=60 RES=0x00 ACK URGP=0
May  3 09:17:05 squidGuard kernel: [64669.158398] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=74.125.95.97 DST=xxx.xxx.xxxx LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=10843 PROTO=TCP SPT=443 DPT=1790 WINDOW=11219 RES=0x00 ACK FIN URGP=0
May  3 09:17:06 squidGuard kernel: [64669.978711] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=209.85.225.83 DST=xxx.xxx.xxxx LEN=1263 TOS=0x00 PREC=0x00 TTL=55 ID=39423 PROTO=TCP SPT=443 DPT=1856 WINDOW=16260 RES=0x00 ACK PSH URGP=0
May  3 09:17:07 squidGuard kernel: [64671.174946] [UFW BLOCK] IN=eth2 OUT= MAC=00:15:5d:04:81:10:00:50:73:f6:f4:a0:08:00 SRC=65.54.95.93 DST=xxx.xxx.xxxx LEN=1500 TOS=0x00 PREC=0x00 TTL=56 ID=15075 DF PROTO=TCP SPT=80 DPT=52652 WINDOW=6335 RES=0x00 ACK URGP=0

 
 
I can do WireShark if that will help, but since it looks as if it is all WAN traffice is having the issue. Would it help?
Thanks for your input

---

### Post by bodhi.zazen on 2011-05-03
all that blocked traffic is on eth2

My guess is you are blocking traffic back from the internet to squid as the ports are high.

---

### Post by w14219 on 2011-05-03
I am trying to locate a document on how to read the log file.  
 
I do not understand what it is telling me.  I was thinking, and what the provider told me, the blocked data was going from the LAN to the WAN. 
 
However, you are thinking it is telling me that the data from the LAN to the WAN is fine, since you see no blocked LAN->WAN data. And that the data from the WAN to the LAN is being blocked?

---

### Post by bodhi.zazen on 2011-05-03
You have a complex network and have not explained your hardware architecture.

I have no idea what traffic is on eth0, eth1, or eth2 , I am simply guessing based on what you have posted.

If it works when you disable your firewall, your firewall is mis-configured.

I have no idea if the traffic that is dropped is legitimate or if it should in fact be blocked.

---

### Post by w14219 on 2011-05-03
Ah. I see. Please allow me.
 
The server has 2 Nics.  
**eth1**=LAN (172.20.0.0)
**eth2**= WAN
 
All LAN clients are on multiple Switchs, same subnet.
 
**I am trying to do the following:**
Firewall: ufw status enabled with the following ports opened....
[B]UFW:
[/B]Status: active
To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
8080                       ALLOW       Anywhere
5900                       ALLOW       Anywhere
5001                       ALLOW       Anywhere
8530                       ALLOW       Anywhere
3389                       ALLOW       Anywhere
21                         ALLOW       Anywhere
5151                       ALLOW       Anywhere
53                         ALLOW       Anywhere
25                         ALLOW       Anywhere
5000                       ALLOW       Anywhere
5002                       ALLOW       Anywhere
5003                       ALLOW       Anywhere
5004                       ALLOW       Anywhere
5005                       ALLOW       Anywhere
 
I need all traffic to pass from ETH2 to ETH1 as I am trying to configure the server as a firewall as well as the proxy server.
 
Everyone on the LAN talks to eth1.
Everyone on the WAN talks to eth2.
 
Initially, I created the rule via iptables forcing all port 80 eth1 to pass WAN data to eth2 port 8080 ([B]iptables -t nat -A PREROUTING -i eth1 -p tcp
--dport 80 -j REDIRECT --to-port 8080[/B]). The problem I then had was that no applications were able to communicate back from the WAN to the LAN. So, I implemented (**iptables -t nat -A POSTROUTING -s 172.20.0.0/16 -j MASQUERADE**) That seemed to work, however, now I am getting the errors in the UFW log.  
 
The input errors are killing my bandwidth.
 
My goal is to allow the above ports to be open, force all internet traffic to 8080, and allow internet applications to connect back to a host on the LAN.
 
It does not sound dificult, but I am really having issues. One after another. 
 
Does that help?

---

### Post by w14219 on 2011-05-06
I believe I got the answer.  It was not related to the Proxy server having issues. It was related to all 150 workstations fighting to the their updates from Microsoft.  
 
Thanks for your support!

---

