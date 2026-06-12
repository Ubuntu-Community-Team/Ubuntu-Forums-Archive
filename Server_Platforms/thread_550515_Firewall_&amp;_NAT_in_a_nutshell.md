---
title: "Firewall &amp; NAT in a nutshell"
date: 2007-09-13
forum: Server Platforms
---

### Post by reloded on 2007-09-13
Hello people. 
I've been reading up and down about NAT and firewall. 
After torrid searching, I found this really neat firewall & NAT program. It is so simple to setup it is shocking! The thing is, I found it after hours of searching? Have you people heard of it? How good is it? It calls itself Ubuntu-Firewall and can be found at [http://rob.pectol.com/content/view/2/1/]("http://rob.pectol.com/content/view/2/1/")
.
I used it to configure the following LAN scenario
Main Network: 192.168.56.0
New network: 172.16.1.0
So, the server sits between the 172.16.1.0 network and the 192.168.56.0 network. Its meant to provide NAT and firewall services. 
The Internet server is found on 192.168.1.1 which is the gateway. The ubuntu server is the PDC & DHCP for the 172.16.1.0 network. It has two NICs. One is configured as 172.16.1.1 (eth0) and the other is 192.168.56.60 (eth1). However, after setting up the above program, I can't access the internet from the 172.x.x.x network. The ubuntu server itself can access the internet through the 192.168.1.1 gateway.

This is what my logs have -and as a newbie, I can't understand nothing!: (the log is the sys log so there might be extra stuff in it)

> Sep 14 06:36:16 vassrv kernel: [44564.169730] ll header: ff:ff:ff:ff:ff:ff:00:10:b5:11:b0:49:08:06
Sep 14 06:36:17 vassrv kernel: [44565.167450] martian source 192.168.56.154 from 192.168.56.160, on dev eth0
Sep 14 06:36:17 vassrv kernel: [44565.167456] ll header: ff:ff:ff:ff:ff:ff:00:10:b5:11:b0:49:08:06
Sep 14 06:37:00 vassrv kernel: [44608.059696] Fell off output chain: IN= OUT=vmnet8 SRC=172.16.250.1 DST=172.16.250.255 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=221 
Sep 14 06:37:00 vassrv kernel: [44608.060043] Fell off output chain: IN= OUT=vmnet1 SRC=172.16.183.1 DST=172.16.183.255 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=221 
Sep 14 06:37:24 vassrv kernel: [44632.514962] Fell off input chain: IN=eth2 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:29:c0:f3:3d:08:00 SRC=172.16.1.101 DST=172.16.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=1697 PROTO=UDP SPT=138 DPT=138 LEN=209 
Sep 14 06:37:34 vassrv kernel: [44642.491104] Fell off output chain: IN= OUT=vmnet8 SRC=172.16.250.1 DST=172.16.250.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep 14 06:37:34 vassrv kernel: [44642.491366] Fell off output chain: IN= OUT=vmnet1 SRC=172.16.183.1 DST=172.16.183.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep 14 06:38:06 vassrv dhcpd: Wrote 0 deleted host decls to leases file.
Sep 14 06:38:06 vassrv dhcpd: Wrote 0 new dynamic host decls to leases file.
Sep 14 06:38:06 vassrv dhcpd: Wrote 2 leases to leases file.
Sep 14 06:38:06 vassrv dhcpd: DHCPREQUEST for 172.16.1.101 from 00:0c:29:c0:f3:3d (SRV2003) via eth0
Sep 14 06:38:06 vassrv dhcpd: DHCPACK on 172.16.1.101 to 00:0c:29:c0:f3:3d (SRV2003) via eth0
Sep 14 06:38:56 vassrv dhcpd: DHCPREQUEST for 172.16.1.100 from 00:0c:29:13:d6:9a (compxp) via eth0
Sep 14 06:38:56 vassrv dhcpd: DHCPACK on 172.16.1.100 to 00:0c:29:13:d6:9a (compxp) via eth0
Sep 14 06:39:01 vassrv /USR/SBIN/CRON[7595]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Sep 14 06:40:47 vassrv kernel: [44834.287002] Fell off input chain: IN=eth2 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:29:c0:f3:3d:08:00 SRC=172.16.1.101 DST=172.16.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=1699 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep 14 06:40:47 vassrv kernel: [44834.288406] Fell off input chain: IN=eth2 OUT= MAC=00:10:b5:11:b0:49:00:0c:29:c0:f3:3d:08:00 SRC=172.16.1.101 DST=172.16.1.1 LEN=112 TOS=0x00 PREC=0x00 TTL=128 ID=1701 DF PROTO=TCP SPT=1094 DPT=139 WINDOW=64240 RES=0x00 ACK PSH URGP=0 
Sep 14 06:40:50 vassrv kernel: [44837.187026] Fell off input chain: IN=eth2 OUT= MAC=00:10:b5:11:b0:49:00:0c:29:c0:f3:3d:08:00 SRC=172.16.1.101 DST=172.16.1.1 LEN=112 TOS=0x00 PREC=0x00 TTL=128 ID=1702 DF PROTO=TCP SPT=1094 DPT=139 WINDOW=64240 RES=0x00 ACK PSH URGP=0 
Sep 14 06:40:50 vassrv kernel: [44837.875516] Fell off input chain: IN=eth2 OUT= MAC=00:10:b5:11:b0:49:00:0c:29:c0:f3:3d:08:00 SRC=172.16.1.101 DST=172.16.1.1 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=1703 DF PROTO=TCP SPT=1094 DPT=139 WINDOW=64240 RES=0x00 ACK URGP=0 
Sep 14 06:42:27 vassrv kernel: [44934.086062] martian source 172.16.1.255 from 172.16.1.1, on dev eth2
Sep 14 06:42:27 vassrv kernel: [44934.086072] ll header: ff:ff:ff:ff:ff:ff:00:14:2a:c6:5d:ca:08:00
Sep 14 06:42:27 vassrv kernel: [44934.086103] martian source 172.16.1.255 from 172.16.1.1, on dev eth2
Sep 14 06:42:27 vassrv kernel: [44934.086107] ll header: ff:ff:ff:ff:ff:ff:00:14:2a:c6:5d:ca:08:00
Sep 14 06:42:27 vassrv kernel: [44934.087755] Fell off output chain: IN= OUT=vmnet8 SRC=172.16.250.1 DST=172.16.250.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep 14 06:42:27 vassrv kernel: [44934.087943] Fell off output chain: IN= OUT=vmnet1 SRC=172.16.183.1 DST=172.16.183.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep 14 06:42:30 vassrv kernel: [44937.049739] Fell off input chain: IN=eth2 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:29:13:d6:9a:08:00 SRC=172.16.1.100 DST=172.16.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=407 PROTO=UDP SPT=138 DPT=138 LEN=209 
Sep 14 06:42:50 vassrv kernel: [44957.260014] Fell off input chain: IN=eth2 OUT= MAC=00:10:b5:11:b0:49:08:00:46:c0:56:e9:08:00 SRC=172.16.1.2 DST=172.16.1.1 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=57219 DF PROTO=TCP SPT=4030 DPT=902 WINDOW=64131 RES=0x00 ACK URGP=0 
Sep 14 06:43:06 vassrv dhcpd: DHCPREQUEST for 172.16.1.101 from 00:0c:29:c0:f3:3d (SRV2003) via eth0
Sep 14 06:43:06 vassrv dhcpd: DHCPACK on 172.16.1.101 to 00:0c:29:c0:f3:3d (SRV2003) via eth0

Honestly, I've been reading about iptables and can't seem to get them to work. Is there an easy way to setup the above scenario? but check out that firewall/NAT program. Its really nice if only it could work.

Thanks.

PS: 
There is no GUI. its all from console.
I've tried shoreline firewall from webmin and I wasn't comfortable setting it up.

---

### Post by reloded on 2007-09-14
Hey, on my DHCP server I had a small but VERY significant typo.
Coz of being used to 192.168.x.x, I had input default gateway to 172.168.x.x instead of 172.16.x.x
So, now, from the 172.168.1.0 network, I can ping the 192.168.56.160 NIC! and all the other NICs on that segment! More importantly, they can't ping me! :)

Everything is working!
The Big Question:
The 192.168.56.1 is the gateway and proxy server. 
On my ubuntu server, it is configured to use proxy server. All PCs on the 192.168.x.x network have 192.168.56.1 as their default gateway and importantly, as the Proxy (in internet explorer, 192.168.56.1: 3128) is configured.

So, being that the 172 network is behind my 172.168.1.1 server, should the PCs in that network  use the 192.168.56.1:3128 as their proxy server?
For your info, when I don't specify the proxy server, I cannot access the internet. When I specify the 192.168.56.1:3128 as their proxy server, I CAN access the internet. Now, I thought that my 172 network would think the 172.16.1.1 gateway was offering everything for them? Why do they have to specify 192.168.1.1 as their proxy server? Isn't that a "hole"?

Thanks.

PS: Am not a salesperson but I wish I was for such a deadly solution. I'd really suggest you try the program: **[Ubuntu-Firewall]("http://rob.pectol.com/content/view/2/1/")**
It took me 2 minutes to configure and you configure in ENGLISH not the 'out of this world too much for newbies ip tables' language.
This is what they describe it as:
> This firewall has been designed to be called directly by the init processes and only requires a simple config file.  It is designed to protect a workstation or server.  As such, it's more of an, "install it and forget it" firewall solution.  You won't get fancy pop-up windows telling you that it just blocked a "hack attempt" or similar -it has logs though which you could inspect-.  What you will get is a powerful and robust firewall that will silently and faithfully inspect each and every packet that enters your Ubuntu Box!  Simple, yet effective! 

It ROCKS! :guitar:

But for the more adept of you, could you please asses the program and tell the rest of us if it is what they claim? Secure, stable, reliable?

---

### Post by reloded on 2007-09-16
Hi lads.
The NAT issue above is solved. Clean and dry. 
But the Proxy question? Any takers?

Do I have to configure my own proxy server for the 172. network to use?
Squid?

---

### Post by HermanAB on 2007-09-16
Hmm, it looks like you are on your way and got things under control.  Just read the iptables man page about 5 times.  It will begin to make sense eventually, then you can try a few things on the command line.

Later, go to tldp.org and read the Advanced Routing Howto.  You will have to read that several times too - over the course of several weeks.  This stuff isn't easy, but once you know it all, people will pay you tons of money to do network administration so it can be worth it in the end.

Cheers,

H.

---

