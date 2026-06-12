---
title: "Problem on configuring /etc/squid/squid.cont"
date: 2008-05-03
forum: Server Platforms
---

### Post by satimis on 2008-05-03
Hi folks,


Ubuntu 6.05.3 server drake


Following Configuration on;
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/squid.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/squid.html)


encountered problem on running;
$ sudo /etc/init.d/squid restart```

 * Restarting Squid HTTP proxy squid                                                                                  2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'acl'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'biz_hours'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'time'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'M'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'T'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'W'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'T'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: 'F'
2008/05/04 02:45:57| aclParseIpData: Bad host/IP: '9:00-17:00'
2008/05/04 02:45:57| ACL name 'biz_hours' not defined!
FATAL: Bungled squid.conf line 1896: http_access allow biz_network biz_hours
Squid Cache (Version 2.5.STABLE12): Terminated abnormally.
                                                                                                               [fail]

```


$ ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:FE:DA:87  
          inet addr:192.168.0.52  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fefe:da87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1704476 (1.6 MiB)  TX bytes:1111100 (1.0 MiB)
          Interrupt:217 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KiB)  TX bytes:5176 (5.0 KiB)

```

Please advise where shall I check and how to rectify the problem?  TIA


B.R.
satimis

---

### Post by andguent on 2008-05-03
The first thing that jumps out at me is that guide has a typo. If you followed it exactly, it appears to have led you slightly astray. The line:
```
acl biz_network src 10.1.42.0/24 acl biz_hours time M T W T F 9:00-17:00
```

should really be:
```
acl biz_network src 10.1.42.0/24
acl biz_hours time M T W T F 9:00-17:00
```

This type of error is very easy to do in a wiki. If changing that doesn't fix your problem, then post your squid.conf and we can go from there.

---

### Post by satimis on 2008-05-03
> **andguent said:**
> The first thing that jumps out at me is that guide has a typo. If you followed it exactly, it appears to have led you slightly astray. The line:
```
acl biz_network src 10.1.42.0/24 acl biz_hours time M T W T F 9:00-17:00
```

should really be:
```
acl biz_network src 10.1.42.0/24
acl biz_hours time M T W T F 9:00-17:00
```

This type of error is very easy to do in a wiki. If changing that doesn't fix your problem, then post your squid.conf and we can go from there.
Thanks for your advice.

Change the line as advised.


$ sudo /etc/init.d/squid restart```

 * Restarting Squid HTTP proxy squid
2008/05/04 06:03:39| aclParseIpData: Bad host/IP: 'acl'
                                          [ ok ]

```
Problem gone.  But there is still a mistake "Bad host/IP".  What dose it mean?  How to fix it?  Thanks


B.R.
satimis

---

### Post by andguent on 2008-05-03
I would need to see your squid.conf to really understand what it is baulking on.

You can post the entire file, or for ease of readability you could post the result of the following command:
**grep -v ^# /etc/squid/squid.conf |grep .**

That command just filters out all of the comments and blank lines.

---

### Post by satimis on 2008-05-03
> **andguent said:**
> I would need to see your squid.conf to really understand what it is baulking on.

You can post the entire file, or for ease of readability you could post the result of the following command:
**grep -v ^# /etc/squid/squid.conf |grep .**

That command just filters out all of the comments and blank lines.
$ sudo grep -v ^# /etc/squid/squid.conf | grep .```

http_port 8888
visible_hostname weezie
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https, snews
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
acl fortytwo_network src 192.168.42.0/24
acl biz_network src 10.1.42.0/24 acl 
acl biz_hours time M T W T F 9:00-17:00
http_access allow fortytwo_network
http_access allow biz_network biz_hours
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid

```

---

### Post by andguent on 2008-05-03
> acl biz_network src 10.1.42.0/24 acl

I think you probably need to drop the extra 'acl' from the end of that line. 'acl' is a keyword that usually needs to be only at the beginning of the line.

Also, you may need to update the network IP ranges based on your environment. Keep in mind that the above line will only apply if the person being filtered is on the 10.1.42.* network. If your internal network where your employees (or kids) are working from is 192.168.0.* or something, some adjustment may be needed.

---

### Post by satimis on 2008-05-03
> **andguent said:**
> I think you probably need to drop the extra 'acl' from the end of that line. 'acl' is a keyword that usually needs to be only at the beginning of the line.

Made correction as advised.


$ sudo /etc/init.d/squid restart```

 * Restarting Squid HTTP proxy squid         [ ok ] 

```

Problem solved.  Thanks


> 
Also, you may need to update the network IP ranges based on your environment. Keep in mind that the above line will only apply if the person being filtered is on the 10.1.42.* network. If your internal network where your employees (or kids) are working from is 192.168.0.* or something, some adjustment may be needed.
Here the network is```

192.168.0.10/50

```
Shall I change it as;```

192.168.0.*
```
?

TIA


[Edit]
Is there any way I can correct the typo on the GUIDE?  So that other folks won't fall into the same mistake.


satimis

---

### Post by andguent on 2008-05-03
> eth0      Link encap:Ethernet  HWaddr 00:13:D4:FE:DA:87  
inet addr:192.168.0.52  Bcast:192.168.0.255  Mask:255.255.255.0
Thank you for posting your ifconfig dump. I've already referred to it a few times to understand your network layout.

Based on this output of eth0, I would suspect you are a 192.168.0.0/24 network. The designation of /24 is the same as having the subnet mask of 255.255.255.0. All computers on the network should have the same subnet mask. They probably all do. Ingore my 192.168.0.* notation, as it is a lazy slang for 192.168.0.0/24. I just think it is more readable.

When you have a line in your conf that says 
**acl biz_network src 10.1.42.0/24**
You are simply taking all traffic from any computer showing itself as 10.1.42.1 through 10.1.42.254 and tagging their connections with the name 'biz_network' for making rules on it later. If your computers are all 192.168.0.1 through 192.168.0.254, the connections from your computers will never get tagged as 'biz_network', and never have any rules applied to it related to 'biz_network'.

I hope I wrote all of that clearly.

The short answer to your question is, yes, you need to change any IP address range on an acl line to 192.168.0.0/24 to have the http_access rules apply. This is true unless you have a much more complicated network then I suspect.

---

### Post by satimis on 2008-05-04
> **andguent said:**
> Based on this output of eth0, I would suspect you are a 192.168.0.0/24 network. The designation of /24 is the same as having the subnet mask of 255.255.255.0. All computers on the network should have the same subnet mask. They probably all do. Ingore my 192.168.0.* notation, as it is a lazy slang for 192.168.0.0/24. I just think it is more readable.

Edit /etc/squid/squid.conf

Changing the lins```

acl biz_network src 10.1.42.0/24

```


as;```

acl biz_network src 192.168.0.0/24

```


A side question.  Does src represent "source" here?


$ sudo /etc/init.d/squid restart```

 * Restarting Squid HTTP proxy squid                        [ ok ] 

```


The router is supplied by ISP, password locked.

They use 192.168.0.1 as gateway.


Router config
```

Start IP Address:	  192.168.0.2	 	 
Number  of  Address:	  50

```


They told me running 51/52/etc. for server IP.


Tried follows w/o success.


$ sudo nano /etc/squid/squid.conf

changing the line```

acl biz_network src 10.1.42.0/24

```

as;```

acl biz_network src 192.168.0.0/50

```

$ sudo /etc/init.d/squid restart```

 * Restarting Squid HTTP proxy squid                                                        
2008/05/05 04:10:43| decode_addr: Invalid IP address '50'
2008/05/05 04:10:43| squid.conf line 1866: acl biz_network src 192.168.0.0/50
2008/05/05 04:10:43| aclParseIpData: Ignoring invalid IP acl entry: unknown netmask '50'
2008/05/05 04:10:43| aclParseAclLine: WARNING: empty ACL: acl biz_network src 192.168.0.0/50		[ ok ]

```

It complains.


Others noted with thanks.


B.R.
satimis

---

### Post by andguent on 2008-05-04
```
acl biz_network src 192.168.0.0/24
```

This is correct. The /24 notation gets into understanding the mechanics behind IP addresses. The short answer is that /24 simply means that all computers on your lan all have their IP address start with 192.168.0. --- The last number designates which actual device it is, and the beginning part designates that it is the same LAN as everyone else.

This works fine as long as you have less than 254 devices on your LAN.

> A side question. Does src represent "source" here?
This is also correct. When a computer on your LAN requests that squid go fetch a web page for them, squid considers them to be the source of that request. The page they are actually requesting is the destination, or 'dst' in squid.conf configurations.

After searching a while for a good explanation of how all of this works, one of the better ones I found was this link below. It explains more of how the options work, and what you can customize to get it doing what you want. Ignore the iptables stuff for now.
[http://www.brennan.id.au/11-Squid_Web_Proxy.html#access](http://www.brennan.id.au/11-Squid_Web_Proxy.html#access)

Admittedly it could be more readable and explain more examples, but I'm not finding much better with only a few minutes of searching.

---

