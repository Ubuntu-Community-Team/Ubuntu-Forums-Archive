---
title: "Why is my ISP portmapping me?"
date: 2007-06-08
forum: Server Platforms
---

### Post by 67GTA on 2007-06-08
I installed Firestarter for fun and to see who was trying to get in. My satellite modem has it's own firewall, so my public IP address is hidden. The only hit I have gotten(about 15-20 per day) is from my ISP. I'm wonderingif they are using linux servers lol. They are getting through the modem and are pinging my public IP. Firestarter is blocking it at that point. Why would they need to portmap my PC? By the way, I'm am not running any servers.

---

### Post by Mr. C. on 2007-06-08
Your public address is *never* hidden... a hint is the word "public".

Your ISP may be testing for commonly open/used ports that are currently being exploited.  Some ISPs do audits.

MrC

---

### Post by Yoooder on 2007-06-08
another possibility that expands upon this is that some ISPs check to see if you are running services/servers on common ports.  Many broadband providers get upset by web/ftp servers running on their residential lines.

---

### Post by Mr. C. on 2007-06-08
Exactly.  That's what I was implying by "audit".

MrC

---

### Post by 67GTA on 2007-06-08
Well, I'm not letting them in. As long as my DHCP lease is renewed like it should be, they can keep knocking. I'm glad to see the firewall is working. It took me a while to catch on to the modem properties. When I would do a port scan the modem IP was scanned and not my IP. Every time I used an online port scan it would say all ports were open. Now I should be running incognito:)

---

### Post by nixfaced on 2007-06-08
The key word I'm seeing in your original post is "pinging".  Is your ISP just pinging you, or performing actual port scans?  If actual port scans, which ports?  If they're just pinging you, it could simply be part of an automated monitoring system, e.g. if X number of hosts are down on a given subnet or network segment, there could be outage issues.

---

### Post by 67GTA on 2007-06-08
I'm not entirely sure. I'm not real technical in that area. I call it "pinging", but not really sure. If I understand what portmap means, then they are trying to map my PC ports? The info Firestarter is giving me is:

direction:unknown
in:eth0
port:30,000's(tried different ports in that range each time)
destination:my IP address
protocol:UDP
service:Sun-RPC portmap

---

### Post by 67GTA on 2007-06-08
I am using Wildblue satellite connection. When I run the IP that Firestarter is blocking with Whois is gives me this:

61.80.213.12.in-addr.arpa. 86400 IN PTR  vip-cdns.syr.wldblu.net
80.213.12.in-addr.arpa 86400 IN NS cdns01.syr.wldblu.net

---

### Post by nixfaced on 2007-06-08
That's interesting... IIRC, the example you listed (sun-rpc portmap) is port 111, and is part of a suite of network services that have largely fallen out of usage.  I can think of a few worms over the years that exploited that service, though.   Are these definitely coming from your ISP?  Or just computers that happen to be on the same ISP you're on?  If they're coming directly from systems that are part of your ISP (dns or mail servers, that sort of thing) then that's a problem and you may want to give their tech support a call and give them a heads-up or at least try and figure out what the deal is.  

If they're coming from a system that's using the same ISP you are, that just means it's likely a compromised computer looking for new computers to portscan.  If you're running a vanilla Ubuntu install (no server software installed after the fact) that shouldn't be a problem, and you'll see much more of the same as time goes on.

---

### Post by Mr. C. on 2007-06-08
portmap is an RPC (eg. used with services such as NFS) protocol multiplexer.

I think you mean port scanning.

Port scanning is simply making network connections to a system's networking ports, in an attempt to find which ports are open, and what services are behind those ports.

Ping (ICMP message) is a simple packet sent to a system requesting an acknowledgment packet in return.  One does not typically ping a port, as ICMP is a different layer than say a TCP packet with a port.

In any event, don't be alarmed at the various probe attempts.  Build your network and they will come.

MrC

---

### Post by 67GTA on 2007-06-08
Is there a GUI app that will let me manipulate ports? If not maybe a guide to a CLI method?

---

### Post by Mr. C. on 2007-06-08
"Manipulating" a port doesn't make sense.  A port is a portion of the TCP/IP network addressing scheme to make connections to / from.  It makes as much sense to manipulate a port as it does to manipulate the street addresses of your home and your neighbor's homes.

---

### Post by 67GTA on 2007-06-08
Bad choice of words. How can I see if any ports are open or listening for something outside my PC?

---

### Post by Mr. C. on 2007-06-08
This will do you:

```
netstat -l --tcp --udp

```
Try this and then open a connection to your box:

```
watch -n 1 netstat -an --tcp --udp
```

Watch the ports come and go.

MrC

---

### Post by 67GTA on 2007-06-08
I have gotten 13 hits from that IP while we have been conversing. They have gone from port 32839>32849>32916>32923>32926>32960....
Maybe I should kill the icon and quit worrying about it.:D

---

### Post by 67GTA on 2007-06-08
They were all familiar except for one. Under "state" it said established and then SYN-SENT on port 110. Whois info on IP:


OrgName:    SISNA 
OrgID:      SISN
Address:    265 East 100 South
Address:    Suite 240
City:       Salt Lake City
StateProv:  UT
PostalCode: 84111
Country:    US

NetRange:   216.126.192.0 - 216.126.239.255 
CIDR:       216.126.192.0/19, 216.126.224.0/20 
NetName:    SISNA-IP
NetHandle:  NET-216-126-192-0-1
Parent:     NET-216-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.SISNA.COM
NameServer: NS2.SISNA.COM
Comment:    ADDRESSES WITHIN THIS BLOCK ARE NON-PORTABLE
RegDate:    1999-07-02
Updated:    2004-09-07

RTechHandle: IPADM146-ARIN
RTechName:   IPADMIN 
RTechPhone:  +1-801-924-0900
RTechEmail:  [email]ipadmin@ikano.com[/email] 

OrgTechHandle: IPADM146-ARIN
OrgTechName:   IPADMIN 
OrgTechPhone:  +1-801-924-0900
OrgTechEmail:  [email]ipadmin@ikano.com[/email]

# ARIN WHOIS database, last updated 2007-06-08 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

Seems it is an ISP company per Google. I will have to find out if they are connected to Wildblue. Thank you for the commands. I will put them in my big book of commands.

---

### Post by Mr. C. on 2007-06-08
110 is POP mail.  One would presume your desktop connected to download pop email.

MrC

---

### Post by 67GTA on 2007-06-08
You nailed it Mr. C. I found out that wildblue uses a third party mail server(pop3). I use gnubiff to check the server for mail.

---

### Post by 67GTA on 2007-09-04
Well, after two months of my ISP spying on me they finally changed tactics. Now instead of SUN-RPC portmap, they are trying to use traceroute. They also have been using something I have never heard of called Trinity v3. Does anyone know what this is?

---

### Post by hellonull on 2007-09-04
[http://xforce.iss.net/xforce/alerts/id/advise59](http://xforce.iss.net/xforce/alerts/id/advise59)

---

### Post by 67GTA on 2007-09-04
I don't seem to have any signs of that. The source is Wildblue's DNS (12.213.80.61). It is always coming "in" on my eht0 connection. I guess Firestarter could have made a mistake. I've seen Trinity v3 and Traceroute as the "service"  a few times the past couple of days, but it is always from my ISP:

Time:Sep  4 15:53:09 Direction: Unknown In:eth0 Out: Port:32796 Source:vip-cdns.syr.wldblu.net Destination:192.168.0.100 Length:151 TOS:0x00 Protocol:UDP Service:Sun-RPC portmap
Time:Sep  4 15:53:30 Direction: Unknown In:eth0 Out: Port:32849 Source:12.213.80.61 Destination:192.168.0.100 Length:123 TOS:0x00 Protocol:UDP Service:Sun-RPC portmap
Time:Sep  4 16:04:23 Direction: Unknown In:eth0 Out: Port:32985 Source:12.213.80.61 Destination:192.168.0.100 Length:210 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep  4 16:16:51 Direction: Unknown In:eth0 Out: Port:33002 Source:12.213.80.61 Destination:192.168.0.100 Length:139 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep  4 16:16:51 Direction: Unknown In:eth0 Out: Port:33003 Source:12.213.80.61 Destination:192.168.0.100 Length:66 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep  4 16:24:23 Direction: Unknown In:eth0 Out: Port:33011 Source:12.213.80.61 Destination:192.168.0.100 Length:127 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep  4 16:27:06 Direction: Unknown In:eth0 Out: Port:33025 Source:12.213.80.61 Destination:192.168.0.100 Length:156 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep  4 16:38:24 Direction: Unknown In:eth0 Out: Port:33039 Source:12.213.80.61 Destination:192.168.0.100 Length:149 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep  4 16:52:17 Direction: Unknown In:eth0 Out: Port:33042 Source:12.213.80.61 Destination:192.168.0.100 Length:383 TOS:0x00 Protocol:UDP Service:Unknown

---

