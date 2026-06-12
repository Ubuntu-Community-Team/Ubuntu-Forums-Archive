---
title: "UFW log guide/tutorial ?"
date: 2012-11-17
forum: Security
---

### Post by cogset on 2012-11-17
Can please someone point me to some kind of beginner's guide/tutorial to  read UFW log messages ? I've  set up some basic rules in UFW,but then  when looking at the log messages I frankly don't understand what I  see,can't figure out what things like AUDIT,DST,TOS actually  are,therefore I can't check if said rules are indeed doing what I  wanted.Thanks.

---

### Post by wildmanne39 on 2012-11-17
*Thread moved to **Security Discussions**.*

---

### Post by Frogs Hair on 2012-11-17
[Here]("https://help.ubuntu.com/community/UFW") is some community documentation , excuse me if you have seen it already.

---

### Post by cogset on 2012-11-18
Thanks,I've read that page but there's no key in it to understand UFW logs.
I've  specifically asked about logs because at this point I'm kinda stuck,as  I've started to add my firewall rules  but then -not knowing how to read  the logs- I can't decipher whether they are actually doing what I  intended or something else or maybe nothing at all ;) I've searched the  forums but I couldn't find so far any specific reading on this matter.

---

### Post by Ms. Daisy on 2012-11-18
Bad news: I had the exact same problem and the only solution I found was  to study UDP/TCP/IP traffic & packets.  That only took a few months  of hard-core studying on my part...

Better news:  I can give you a quick rundown. ```
Nov  11 18:24:57 daisy: [ 5287.193460] [UFW BLOCK] IN= OUT=wlan0  SRC=192.168.1.10 DST=300.120.61.72 LEN=60 TOS=0x00 PREC=0x00 TTL=64  ID=47904 DF PROTO=TCP SPT=52279 DPT=9001 WINDOW=14600 RES=0x00 SYN  URGP=0 
```This is an excerpt from my log. Here's what it's telling us.

**date**  It's good practice to watch the dates and times. If things are out of  order or blocks of time are missing then an attacker probably messed with  your logs.

**[UFW BLOCK]** indicates obviously that the packet was blocked.  

**IN= and OUT=wlan0** indicate whether it was incoming or outgoing. So this packet was outbound on my wlan0 connection.

**SRC=192.168.1.10**  This indicates the source IP, who sent the packet initially.  In this  case it was me. Some IPs are routable over the internet, some will only  communicate over a LAN, and some will only route back to the source  computer.  [Here's a handy guide]("http://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses").  

**DST=300.120.61.72**  This indicates the destination IP, who is meant to receive the packet.   (In this case it's fictitious - 255 is the highest number possible in  each octet). You can use whois.net to determine who the IP belongs to  (this one belongs to Swordfish ;) ).

**LEN=60** This indicates the length of the packet.

**TOS** and **PREC** These are details about the packets that aren't really relevant for reading logs. They're set to 0 which means they're not relevant in this particular packet either.  [More here]("http://tools.ietf.org/html/draft-xiao-tcp-prec-02") if you care.

**TTL 64 **=  This indicates the "[Time to live]("http://en.wikipedia.org/wiki/Time_to_live")" for the packet. Basically each packet  will only bounce through the given number of routers before it dies and  disappears.  If it hasn't found its destination before the TTL expires,  then the packet will evaporate.  This field keeps lost packets from clogging the internet forever.

**ID=47904** Not sure what this one is, but it's not really important for reading logs. It might be ufw's internal ID system, it might be the operating system's ID.

**PROTO=TCP** This indicates the protocol of the packet. In this case it was TCP. The other one you'll see is UDP. More explanation [here]("http://www.bleepingcomputer.com/tutorials/tcp-and-udp-ports-explained/").
[B]
SPT=52279[/B] This indicates the source port. My computer generated this packet on port 52279. This is a random high port which is typical.[This is a handy resource]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers")  to determine what services may have started a connection.   In most  connections you'll see one registered port and one high unregistered  one. The server typically uses the registered port & the client uses  the high one.  So in this instance, the source was me and it was a  random high number, so I'm the client.

**DPT=9001** This  indicates the destination port.  The receiving computer is listening on  port 9001 for a connection. This is a registered port for a few  different services, so the destination was the server. I run Tor so I  can make a reasonable assumption that this was a Tor packet. The source & destination port will be the most important fields to understand (along with source & destination IPs) when dissecting firewall logs.

 **WINDOW=14600** This indicates the size of packet the sender is willing to receive.

**RES=0x00** This bit is reserved for future use & is always set to 0. Basically it's irrelevant for log reading purposes.

**SYN URGP=0** SYN indicates that this connection requires the three-way handshake typical of TCP connections. URGP indicates whether the urgent pointer field is relevant. 0 means it's not. Doesn't really matter for firewall log reading.
[COLOR=Red]
Conclusion: If I wanted to use my firewall while using Tor, then I have not set UFW up properly.  I need to add a rule to allow out TCP port 9001.[/COLOR]  I hope that helps.

---

### Post by Ms. Daisy on 2012-11-18
This helped me to understand firewall logs and, more importantly, what's worrisome and what's not:

[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by cogset on 2012-11-19
Thanks a lot for taking the time to explain all this,I was kinda surprised seeing that there's not much documentation around on this matter (or,if there is,it's hidden really well ;) ). 
Please excuse me for shamelessly asking,but could you also briefly explain what log lines like this really mean
[B] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.xxx DST=99.239.231.99(...)
[/B]what is the firewall  doing when I see "AUDIT" in the log,is it  actually dropping or allowing that particular connection?

---

### Post by Ms. Daisy on 2012-11-19
I didn't find any written documentation so I just messed with my own ufw logging levels to see what happens. 

You can set rules in ufw to deny and to allow.  Audit shows connections that were allowed but did not specifically match ufw allowed rules (aside from "allow out all").  If you want to know about every connection your computer makes then audit is handy.  Otherwise it will just fill up your hard drive with logs. You've probably got the logging set to medium or high, which is when audits are reported by ufw.  Change it to low and the audits will go away (they did for me).

```
sudo ufw logging low
```

---

