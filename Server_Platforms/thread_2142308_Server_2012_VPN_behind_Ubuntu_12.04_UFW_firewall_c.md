---
title: "Server 2012 VPN behind Ubuntu 12.04 UFW firewall can't connect from outside"
date: 2013-05-05
forum: Server Platforms
---

### Post by tellme on 2013-05-05
Hi all,

most of the time i solve my ubuntu problems by searching and reading however now i am real stuck for a week.
mail\ftp\www\rds\webmin\ssh portforwarding all works except VPN
I have a virual environment with ubuntu as firewall\gateway. Behind i have a windows server 2012 domain controller server with dhcp and vpn configured.

root@HG-GATEWAY:~# ufw version
ufw 0.31.1-1
Copyright 2008-2010 Canonical Ltd.

I have made the following config with webmin for portforwarding:
-A PREROUTING -p tcp -m tcp -i eth0 --dport 1723 -j DNAT --to-destination 192.168.1.10:1723

I have added these 2 line in the before.rules:
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT

outside ip port is 10.10.10.10 --> eth0
inside network is 192.168.1.0/24 --> eth2


I am strugling a week now to get this working.
Intern network virtual machines can connect to the vpn server.

This is what ufw logging says:
May  5 03:09:44 HG-GATEWAY kernel: [21503.274226] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXX LEN=556 TOS=0x00 PREC=0x00 TTL=123 ID=18144 PROTO=UDP SPT=500 DPT=500 LEN=536 

May  5 03:09:46 HG-GATEWAY kernel: [21505.302020] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXX LEN=556 TOS=0x00 PREC=0x00 TTL=123 ID=18145 PROTO=UDP SPT=500 DPT=500 LEN=536


someone can point me in the right direction,your input is realy appreciated ?

Tellme

---

### Post by tellme on 2013-05-05
Nobody has an UFW firewall with a windows VPN behind running ?? help help !

---

### Post by matt_symes on 2013-05-05
Thread moved to **Server Platforms**.

You may have more luck here.

Network and Wireless is more for hardware, driver problems.

---

### Post by tellme on 2013-05-06
I have now followed this guide:
[http://ubuntuforums.org/showthread.php?t=2071378&highlight=ufw+vpn](http://ubuntuforums.org/showthread.php?t=2071378&highlight=ufw+vpn)


still get in the ufw log file following message:


May  6 22:55:13 HG-GATEWAY kernel: [179033.028899] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23165 PROTO=47 
May  6 22:55:16 HG-GATEWAY kernel: [179036.071192] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23179 PROTO=47 
May  6 22:55:20 HG-GATEWAY kernel: [179040.127241] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23197 PROTO=47 
May  6 22:55:24 HG-GATEWAY kernel: [179044.183387] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23216 PROTO=47 
May  6 22:55:28 HG-GATEWAY kernel: [179048.238983] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23223 PROTO=47 
May  6 22:55:33 HG-GATEWAY kernel: [179052.295100] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23228 PROTO=47 
May  6 22:55:37 HG-GATEWAY kernel: [179056.350889] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23237 PROTO=47 
May  6 22:55:45 HG-GATEWAY kernel: [179064.463032] [UFW BLOCK] IN=eth0 OUT= MAC=00:15:5d:00:c9:21:00:d0:03:1e:10:00:08:00 SRC=195.241.XXX.XXX DST=85.17.XXX.XXXX LEN=57 TOS=0x00 PREC=0x00 TTL=123 ID=23258 PROTO=47 

I have the idea that that POTOCOL 47 is Blocked by UFW, how to open this for all inetrfaces in UFW

---

### Post by darkod on 2013-05-06
I have no idea what protocol 47 is, but the log lines you posted in your first post clearly shows you are trying to use port udp/500 which is the IPsec port. And your DNAT command is for port 1723. Look in the log line DPT=500, that's Destination Port.

Did you try forwarding port 500 too? Depending what you plan to use for the vpn, you need to make sure you are opening and forwarding the correct ports. For example, the default OpenVPN port is udp/1194 so 500 or 1723 wouldn't even apply.

Star from there, what sort of vpn server is it?

---

### Post by tellme on 2013-05-07
> **darkod said:**
> I have no idea what protocol 47 is, but the log lines you posted in your first post clearly shows you are trying to use port udp/500 which is the IPsec port. And your DNAT command is for port 1723. Look in the log line DPT=500, that's Destination Port.

Did you try forwarding port 500 too? Depending what you plan to use for the vpn, you need to make sure you are opening and forwarding the correct ports. For example, the default OpenVPN port is udp/1194 so 500 or 1723 wouldn't even apply.

Star from there, what sort of vpn server is it?

Hi Darkod, thanks for reply !
I have setup windows VPN server running behind the Ubuntu UFW.
When i used the DL380 G6 server at home i had my internet provider router as firewall and used port 1723 to nat to the VPN server.
Now i have moved the server to a co-location in a datacenter and i have installed as router \ gateway UFW running on Ubuntu 12.04
I have NAT all sort of ports like RDS / HTTP / HTTPS / SSH / SMTP ..etc but only VPN is not working...

I got this message trying to connect:

Error 806: a connection between your computer and the VPN server can not be created.  The most common cause for this is that there is at least one internet device between your computer and the VPN server is not configured to allow GRE protocol packets Verify that protocol 47 GRE is allowed on all personal firewall devices or routers.  if the problem persists, contact your administrator.
I don't get any log now back from UFW

This i have in my UFW configured by Webmin::
**Incoming packets (INPUT) - Only applies to packets addressed to this host**
[TABLE="class: ui_table sortable, width: 100%"]
[TR="class: mainhigh, bgcolor: #EFEFEF"]
[TD="width: 10%"][[COLOR=#00aa00]Accept[/COLOR]]("http://ubuntuforums.org/edit_rule.cgi?table=0&idx=9")
[/TD]
[TD]If protocol is **GRE**
[/TD]
[/TR]
[/TABLE]


**Forwarded packets (FORWARD) - Only applies to packets passed through this host**[TABLE="class: ui_table sortable, width: 100%"]
[TR="class: mainhigh, bgcolor: #EFEFEF"]
[TD="width: 10%"][[COLOR=#00aa00]Accept[/COLOR]]("http://ubuntuforums.org/edit_rule.cgi?table=0&idx=9")
[/TD]
[TD]If protocol is **[FONT=Thread-00001380-Id-0000000d]GRE[/FONT]**
[/TD]
[/TR]
[/TABLE]


**Packets before routing (PREROUTING)**
[TABLE="class: ui_table sortable, width: 100%"]
[TR="class: mainhigh, bgcolor: #EFEFEF"]
[TD="width: 10%"]Destination 
NAT
[/TD]
[TD]If protocol is **TCP** and input interface is **eth0** 
and destination port is **1723**
[/TD]
[/TR]
[/TABLE]


/etc/ufw/sysctl.conf:

net/ipv4/ip_forward=1
net/ipv4/conf/all/accept_redirects=0
net/ipv4/conf/default/accept_redirects=0
net/ipv6/conf/all/accept_redirects=0
net/ipv6/conf/default/accept_redirects=0
net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/icmp_echo_ignore_all=0
net/ipv4/conf/all/log_martians=0
net/ipv4/conf/default/log_martians=0


/etc/ufw/before.rules:

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines
# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT
# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT
# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT
#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local
# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT
# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT
# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

What am i missing...

Last login: Tue May  7 00:23:14 2013 from 192.168.XXX.XXX
[EMAIL="root@HG-GATEWAY"]root@HG-GATEWAY[/EMAIL]:~# status ufw
ufw start/running

Before running ths commnd i saw all ports opened, not anymore..............

---

### Post by tellme on 2013-05-07
I have solved the VPN problem, finally !!! I had to NAT protocol GRE to the VPN router, then voilla, immediate connected !!!! FINALLY , it's late, bedtime :-)
Thanks for reading and thinking !!!!

---

