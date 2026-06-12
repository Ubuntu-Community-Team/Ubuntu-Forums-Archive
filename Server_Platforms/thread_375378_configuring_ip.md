---
title: "configuring ip"
date: 2007-03-03
forum: Server Platforms
---

### Post by devious1 on 2007-03-03
I am using a dlink router 604
for my server i have a pentium 3 with a 200 gig drive and 256 m ram running ubuntu server 6.10
and i installed ubuntu from live cd on a pentium2 my other computer in my network use windows 2000 pro and win xp pro

I looked up my ip and tried to follow the steps to resolv.conf when I open my router my 
 	 00-11-95-3d-27-73
IP Address 
	192.168.0.1
Subnet Mask 
	255.255.255.0
DHCP Server 
	Enabled
  	 
WAN
MAC Address 
	00-13-d3-11-75-da
Connection 
	DHCP Client Connected  
IP Address 
	24.12.23.249
Subnet Mask 
	255.255.254.0
Default Gateway 
	24.12.22.1
DNS 
	68.87.72.130 68.87.77.130

I have 2 names I pay for wich are currently in use by my websites I also have a few free from no-ip and a few others. how do i configure nameserver? 
what is the correct way to configure my server or should I start from scratch?

any help is always appreciated

---

### Post by Mr. C. on 2007-03-03
Is your WAN IP static or dynamic ?

I cannot easily tell from :

   c-24-12-23-249.hsd1.il.comcast.net.

If its static, you go to your nameserver's site (I presume you have a nameserver or registar for your names), and configure an A record for your host, and any other records you may want (MX, etc.).  If you want to use names like [www.yourdomain.com](www.yourdomain.com), ftp.yourdomain.com, etc. configure A records for  www, ftp. ...

If your IP is dynamic, you'll have to use one of the DDNS services to place a name to your dynamic IP.

MrC
ps. Please use punctuation.  Long sentences with no periods, or commas are very difficult to read.

---

