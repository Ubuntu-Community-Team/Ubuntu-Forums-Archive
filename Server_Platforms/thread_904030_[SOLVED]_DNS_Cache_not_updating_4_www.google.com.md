---
title: "[SOLVED] DNS Cache not updating 4 www.google.com"
date: 2008-08-28
forum: Server Platforms
---

### Post by DantePasquale on 2008-08-28
Hi All,

I'm having a strange problem. I'm running ISPConfig and have followed the setups for installation of bind9/named in a chrooted environment. All is working quite well, and has been for a couple of years. I'm running 8.04 LTS with the latest bind9/named patches/updated.

When I do an run dig against my own dns server I get different results than when I run dig against my ISP's DSN! 

How do I get my DNS server back in sync with my ISP? I tried reboot, restart and reload and no updates. I also did a cache dump but can't follow that too well.

Here's the output:

```
My ISPs DNS:

; <<>> DiG 9.4.2-P1 <<>> @64.105.179.138 www.google.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10733
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 7, ADDITIONAL: 7

;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		6565	IN	CNAME	www.l.google.com.
www.l.google.com.	109	IN	A	64.233.167.147
www.l.google.com.	109	IN	A	64.233.167.99
www.l.google.com.	109	IN	A	64.233.167.104

;; AUTHORITY SECTION:
l.google.com.		11224	IN	NS	c.l.google.com.
l.google.com.		11224	IN	NS	d.l.google.com.
l.google.com.		11224	IN	NS	e.l.google.com.
l.google.com.		11224	IN	NS	f.l.google.com.
l.google.com.		11224	IN	NS	g.l.google.com.
l.google.com.		11224	IN	NS	a.l.google.com.
l.google.com.		11224	IN	NS	b.l.google.com.

;; ADDITIONAL SECTION:
a.l.google.com.		15254	IN	A	209.85.139.9
b.l.google.com.		11923	IN	A	64.233.179.9
c.l.google.com.		12152	IN	A	64.233.161.9
d.l.google.com.		14176	IN	A	66.249.93.9
e.l.google.com.		10656	IN	A	209.85.137.9
f.l.google.com.		9575	IN	A	72.14.235.9
g.l.google.com.		7709	IN	A	64.233.167.9

;; Query time: 19 msec
;; SERVER: 64.105.179.138#53(64.105.179.138)
;; WHEN: Thu Aug 28 21:35:49 2008
;; MSG SIZE  rcvd: 324
```

```
My DNS:

dante@dexter:~/Desktop$ dig @74.1.46.162 www.google.com

; <<>> DiG 9.4.2-P1 <<>> @74.1.46.162 www.google.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8770
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 7, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		598901	IN	CNAME	www.l.google.com.
www.l.google.com.	300	IN	A	74.125.45.103
www.l.google.com.	300	IN	A	74.125.45.147
www.l.google.com.	300	IN	A	74.125.45.99
www.l.google.com.	300	IN	A	74.125.45.104

;; AUTHORITY SECTION:
l.google.com.		80501	IN	NS	e.l.google.com.
l.google.com.		80501	IN	NS	c.l.google.com.
l.google.com.		80501	IN	NS	b.l.google.com.
l.google.com.		80501	IN	NS	d.l.google.com.
l.google.com.		80501	IN	NS	a.l.google.com.
l.google.com.		80501	IN	NS	g.l.google.com.
l.google.com.		80501	IN	NS	f.l.google.com.

;; Query time: 87 msec
;; SERVER: 74.1.46.162#53(74.1.46.162)
;; WHEN: Thu Aug 28 21:36:20 2008
;; MSG SIZE  rcvd: 228
```

---

### Post by Vegan on 2008-08-29
Are you running a primary or secondary DNS? Looks like a secondary one and as such its not authoritative.

---

### Post by MJN on 2008-08-29
This is perfectly normal behaviour. As you can see from the output Google have a massively distributed DNS and will return different results for different resolvers from different name servers. This spreads the load on their web servers, both geographically (see how the results are tailored close to your netblock) and dynamically (multiple results), and whilst you will hit different web servers you'll still be accessing the same backend.
 
Mathew

---

### Post by DantePasquale on 2008-08-29
OK, I'll buy that idea that google returns many different IP's depending on location, etc. However, why is it that when I use one (not all) of the IPs returned by my DNS that Firefox can't connect?

I've run wireshark to try to see what's going on traffic wise and after the DNS query is returned, all I see is ARP messages, asking who has this one IP, then the next, and so on until the list of IPs is complete? But if I use the IPs returned by my ISP, I see normal TCP/HTTP traffic after the query is returned?

Thanks,
Danté

Oh, and this is ONLY happening with [www.google.com](www.google.com) and rds.yahoo.com. I've found no other names/IP's yet that have this behavior.

---

### Post by MJN on 2008-08-29
Your subnet mask and/or other network configuraiton is screwed up.
 
To give an example, if you are attempting to establish a connection to 74.125.45.103 then your network stack should only be sending out ARP requests if it thinks that this IP address is on its subnet. If the address is known not to be on the local subnet then it should be making ARP requests for the default gateway address as it is to here that the packets will be sent (via Ethernet hence the ARP request).
 
Post the output of **ifconfig /all** and we can take a look.
 
Mathew

---

### Post by DantePasquale on 2008-08-30
That's what I was thinking -- I used to know a lot about network protocols, but that was way long ago.
 
After more investigation here's what I found out. This only happens on my computers that are connected to my wireless, not from the ones that are hardwired. I have a wireless router that I configured as a switch using the suppliers directions. But, I think that's what the problem is! 

**Here's my network info from one of the computers on the wireless**:
```

dante@dexter:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d4:de:dc:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101396 (99.0 KB)  TX bytes:101396 (99.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:f2:90:4d  
          inet addr:74.1.46.173  Bcast:74.255.255.255  Mask:**[COLOR="Red"]255.0.0.0[/COLOR]**
          inet6 addr: fe80::213:e8ff:fef2:904d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92029505 (87.7 MB)  TX bytes:7280120 (6.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-F2-90-4D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dante@dexter:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:13:e8:f2:90:4d  
          inet addr:74.1.46.173  Bcast:74.255.255.255  Mask:[COLOR="Red"]255.0.0.0[/COLOR]
          inet6 addr: fe80::213:e8ff:fef2:904d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92396939 (88.1 MB)  TX bytes:7385001 (7.0 MB)


```



```
dante@dexter:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
74.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 wlan0
0.0.0.0         74.1.46.161     0.0.0.0         UG        0 0          0 wlan0
```

**After trying to get to [www.google.com](www.google.com)**:

```
dante@dexter:~$ arp -an
? (74.125.45.99) at <incomplete> on wlan0
? (74.125.45.103) at <incomplete> on wlan0
? (74.125.45.147) at <incomplete> on wlan0
? (74.1.46.166) at 00:E0:81:72:ED:A5 [ether] on wlan0
? (74.1.46.163) at 00:E0:81:72:ED:A4 [ether] on wlan0
? (74.1.46.162) at 00:E0:81:72:ED:A4 [ether] on wlan0
? (74.1.46.161) at 00:0F:CC:1D:CA:B8 [ether] on wlan0
? (74.125.45.104) at <incomplete> on wlan0
```

**Wireless "router" current config:**

```
Router Status
 
Account Name 	WGR614v7
Hardware Version 	V7
Firmware Version 	V2.0.20_1.0.20NA
 
Internet Port
MAC Address 	00:1B:2F:6C:11:C1
IP Address 	0.0.0.0
DHCP 	DHCPClient
IP Subnet Mask 	0.0.0.0
Domain Name Server
	0.0.0.0
 
LAN Port
MAC Address 	00:1B:2F:6C:11:C0
IP Address 	74.1.46.171
DHCP 	OFF
IP Subnet Mask 	255.255.255.240
```


I can't give the configuration of my main router to Covad as Covad manages that configuration and I don't have access to it.

It looks to me like all the netmasks are configured properly except that **[COLOR="Red"]255.0.0.0[/COLOR]**!!!

I am using "wicd" to configure the wireless as that's the only tool I can get to work on this particular laptop. I guess I've got something mis-configured there and will revisit!

I tracked this down to having a typo in the netmask in wicd. I had 255.255..255.240 so that probably messed it up and defaulted to some class A network! Wow, guess we need some more syntax checking in wicd -- or I should make an /etc/netmasks file and be done with it :)

Thanks for the help on getting me on the right path,
Danté

---

