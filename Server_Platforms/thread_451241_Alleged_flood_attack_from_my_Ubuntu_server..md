---
title: "Alleged flood attack from my Ubuntu server."
date: 2007-05-22
forum: Server Platforms
---

### Post by librano on 2007-05-22
Hello everybody!

I need some help with an alleged flood attack from my IP address. My knowledge of Linux is beginner towards average (just as a gauge as to how easy or complicated your answers should/would be)

I am running a headless Ubuntu 7.04 server which is up to date. This box is a router/gateway machine for my home network. Services on the server include LAMP server (default Ubuntu settings with a few modifications: MySQL not network enabled, etc), Squid transparent proxy server, BIND DNS server, Samba filesharing to LAN only (with login and password), FTP file sharing to LAN only (with login and password), SSH accessible only from LAN (for admin purposes), Webmin accessible only from LAN (for admin purposes), as a firewall I am using Shorewall which allows full access from LAN. From the internet open ports are for Apache and a few ports forwarded to machines on the LAN (mainly for p2p applications). On my LAN I have 2 boxes: one Ubuntu 6.06 and another Windows XP with antivirus and firewall.

As you can see I think I have taken quite a few security measures. However, last night I got a call from my ISP saying that there is a flood attack coming from my IP address. I immediately ifdown-ed the external interface and closed all external ports on Shorewall. I also turned off all non-essential services and only left SSH, Webmin, Squid, BIND DNS, Shorewall only with port redirects for transparent proxying. I restarted the external interface and traffic was only 3kb/s max at idle (no browsing).

Today morning I got another call and my ISP saying that the flood attack is still coming from my IP address and that I they are going to change my IP address (which they did). They told me to check my computer for the malicious software. Being windows-centric their suggestion was to scan for viruses. The only info I could squeeze out of the lady was that there was a flood attack from my IP address.

Now my questions? What is going on? Is it really malicious software running on my Ubuntu server? What about the Windows box on my LAN? How can I verify this and make sure that there is no malicious software on my Linux machines? Is this just some guying spoofing an attack from my IP address?

Any help you can offer will be greatly appreciated. If you require any extra information I am glad to provide it. Thank you.

lib.

---

### Post by DDuong on 2007-05-22
Hello,

Question: When the ISP changed your IP address, did the flooding stop?

---

### Post by Chayak on 2007-05-22
Smoothwall has graphs for your network traffic over time if I remember correctly.  You should be able to look at that and get the supposed times of that flood attack to see if is one of the machines in your network.

Ack shorewall rather, that's what I get for skimming over text

---

### Post by librano on 2007-05-24
hello all

sorry for the delayed reply. my ISPs router had been giving me problems with my new IP address. a page like this one would take 10 minutes to load... anyway that is sorted now...

what i have come up with so far on this matter is that the flooding from my IP address stopped after i had been moved to the new IP address. this leads me to think that somebody was using my DNS server to perform these attacks. I am not very well versed when it comes to DNS servers but from what i have read, this would be caused by a recursive DNS server.

the installation of BIND was with the default settings of Ubuntu 7.04. ie. during installation i selected to install DNS and LAMP servers. this makes me wonder if the default Ubuntu server install has some security flaws.

Concerning my logs, i did not notice anything i would find suspicious... however, i know next to nothing about logs.

here are my BIND configurations.

```
options {
	directory "/var/cache/bind";


	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };

	allow-recursion { localnets; };

	forwarders {
		<extarnal DNS server1>;
		<extarnal DNS server2>
                <extarnal DNS server3>;
		};
	forward first;
};


```

as you can see recursion is only allowed to localnets which i suppose means 127.0.0.1 so i dont know how the attack would have taken place.

here is my shorewall rules file.

```
#p2p to Ubuntu box
DNAT	net	loc:192.168.0.2	tcp	1213	-	<my-external-IP-address>
DNAT	net	loc:192.168.0.2	tcp	1355	-	<my-external-IP-address>
DNAT	net	loc:192.168.0.2	tcp	2441	-	<my-external-IP-address>
DNAT	net	loc:192.168.0.2	tcp	3941	-	<my-external-IP-address>

#p2p to Ubuntu box
DNAT	net	loc:192.168.0.2	tcp	57571	-	<my-external-IP-address>

#p2p to windows box
DNAT	net	loc:192.168.0.3	tcp	15051	-	<my-external-IP-address>

#torrentflux
ACCEPT	net	$FW	tcp	40000:40007

#apache
ACCEPT	net	$FW	tcp	80,443

#squid transparent proxy redirect
REDIRECT	loc	3128	tcp	www

```

again you will notice that the only external port open on my router/server is the apache port. the rest are port forwards to internal boxes.

in general the log files that have had network logs look like this. this one is from my syslog

```
May 23 18:00:00 server kernel: [119882.920678] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=971 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=21779 
May 23 18:00:01 server kernel: [119883.897958] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=972 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=22035 
May 23 18:00:01 server kernel: [119883.923202] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=972 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=22035 
May 23 18:00:02 server /USR/SBIN/CRON[25898]: (root) CMD (/etc/webmin/bandwidth/rotate.pl)
May 23 18:00:02 server kernel: [119884.897837] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=973 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=22291 
May 23 18:00:02 server kernel: [119884.922457] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=973 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=22291 
May 23 18:00:03 server kernel: [119885.897620] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=976 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=22547 
May 23 18:00:03 server kernel: [119885.922147] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=976 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=22547 
May 23 18:00:04 server kernel: [119886.898372] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=977 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=22803 
May 23 18:00:04 server kernel: [119886.922611] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=977 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=22803 
May 23 18:00:05 server kernel: [119887.898176] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=978 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23059 
May 23 18:00:05 server kernel: [119887.922549] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=978 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=23059 
May 23 18:00:06 server kernel: [119888.900042] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=979 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23315 
May 23 18:00:07 server kernel: [119888.924681] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=979 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=23315 
May 23 18:00:07 server kernel: [119889.899859] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=980 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23571 
May 23 18:00:07 server kernel: [119889.923548] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.3 LEN=60 TOS=0x00 PREC=0x00 TTL=243 ID=980 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=23571 
May 23 18:00:07 server kernel: [119890.015080] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.2 DST=<some-IP-address> LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=14368 DF PROTO=TCP SPT=38162 DPT=5050 WINDOW=5050 RES=0x00 ACK PSH URGP=0 
May 23 18:00:08 server kernel: [119890.220299] BANDWIDTH_IN:IN=eth0 OUT=eth1 SRC=<some-IP-address> DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=29157 DF PROTO=TCP SPT=5050 DPT=38162 WINDOW=33304 RES=0x00 ACK URGP=0 
May 23 18:00:08 server kernel: [119890.900561] BANDWIDTH_OUT:IN=eth1 OUT=eth0 SRC=192.168.0.3 DST=<some-IP-address> LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=981 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23827 

```

i couldn't figure out how to work netstat but the problem went away  by the time i had the internet up and running... so there wasnt much incentive.

hope i have given enough information to kick up a discussion. if you need more information please ask.

if you see any discrepancies or a cause for this attack please post  so that i can avoid future attacks... and maybe help others using Ubuntu as a server.

thanks for your help and suggestions.

lib.

---

### Post by cprofitt on 2007-06-11
Hmm...

Its also possible that someone was doing a man-in-the-middle attack -- not using your server, but just injecting their packets and tagging them with your IP address.

---

