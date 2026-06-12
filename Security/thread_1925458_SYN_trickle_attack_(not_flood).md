---
title: "SYN trickle attack (not flood)"
date: 2012-02-14
forum: Security
---

### Post by Doug S on 2012-02-14
Hi,
I am having what I have termed a SYN trickle attack. SYN packets to my public facing web server at a low rate of only several per minute.
This type of event is rare, and I have only noticed it two previous times (on and about 2007.08.11, and 2010.02.20)( which doesn't mean I might have missed some occurences).
What baffles me with this event is: What is the purpose? I simply have not been able to figure the reason for it.
The one idea I had was that perhaps the return address is forged and the real attack is against that forged address. By sending one SYN packet to a web site, the attcker will typically get 6 packets sent to the forged address, as it re-tries do to no response. Therefore achieving a gain factor of 6 on their ability to flood the desired ip address, as well as better anonymity. For example:```
2012-02-13 08:02:42.201860 IP 75.87.211.76.0 > 209.121.28.192.80: Flags [S], seq 0, win 65535, length 0
2012-02-13 08:02:42.201913 IP 209.121.28.192.80 > 75.87.211.76.0: Flags [S.], seq 3862072714, ack 1, win 5840, options [mss 1460], length 0
2012-02-13 08:02:46.247904 IP 209.121.28.192.80 > 75.87.211.76.0: Flags [S.], seq 3862072714, ack 1, win 5840, options [mss 1460], length 0
2012-02-13 08:02:52.247895 IP 209.121.28.192.80 > 75.87.211.76.0: Flags [S.], seq 3862072714, ack 1, win 5840, options [mss 1460], length 0
2012-02-13 08:03:04.247909 IP 209.121.28.192.80 > 75.87.211.76.0: Flags [S.], seq 3862072714, ack 1, win 5840, options [mss 1460], length 0
2012-02-13 08:03:28.247900 IP 209.121.28.192.80 > 75.87.211.76.0: Flags [S.], seq 3862072714, ack 1, win 5840, options [mss 1460], length 0
2012-02-13 08:04:16.447909 IP 209.121.28.192.80 > 75.87.211.76.0: Flags [S.], seq 3862072714, ack 1, win 5840, options [mss 1460], length 0

```In this case the packets use illegal port addresses as well as legal ones, so I have added iptables rules to identify, and thereafter drop, the bad address (which changes a couple of times a day).
I was just wondering if anyone elese has seen this type of thing and or has an opinion as to what its purpose might be.

---

### Post by perspectoff on 2012-02-14
Heh heh. Every time I think that is happening to me I discover it's just the Google spider. 

The Google spider will slow my server all day (but I have hundreds of web pages on my site).

---

### Post by Doug S on 2012-02-14
Hi perspectoff, and thanks for your reply.
However, I believe you have misunderstood my posting. The additional load on my system due to this is negligible. And actually the tcp session never even completely opens. The only reason I even notice this "SYN trickle attack", as I call it, is due the exceptionally high NEW port 80 connections as shown in my iptables rule set counters. I would guess that most server administrators would not even notice.

---

### Post by emiller12345 on 2012-02-15
If the problem is just that it is spamming your log files, then take a look at the 'limit' property of iptables. 
[https://help.ubuntu.com/community/IptablesHowTo#Logging](https://help.ubuntu.com/community/IptablesHowTo#Logging)
or man iptables
It will limit how many entries will show up in your log with out sacrificing notification.

---

### Post by Doug S on 2012-02-19
Hi emiller12345,
 
No, it is not an excess logging issue. Actually, I have worked to increase, rather than decrease, the number of log entries related to this issue. 
 
By the way, this latest occurance has now ended.
 
As mentioned in my OP (Original Posting), I was just inquiring to the forum community if others have seen similar or have an opinion as to what is the purpose.

---

### Post by emiller12345 on 2012-02-21
I see. You have a rule to only allow high port number <-> port 80 and this is trying to connect **Port Zero** to port 80.

[http://www.grc.com/port_0.htm](http://www.grc.com/port_0.htm)

According to GRC, port zero is 'an invalid port number'. I think I remember reading somewhere it's used as a system port or maybe its used internally by the kernel? What ever the case, these look like malformed packets.

---

### Post by Doug S on 2012-04-01
I'm setting this thread to solved, as it seems to have been of little interest to others.
It remains of interest to me, but I would be the first to admit that I am fanatical about looking through my logs. Since the original postings, there was only one more occurence (after I had removed my temporary detect and drop rule in iptables). 2680 incoming and 7082 outgoing packets, which isn't a gain factor of 6, but that is becuase the illegal port ones don't seem to repeat and sometimes the same port is used again to soon and such. Incoming packet rate was only 16.6 packets per minute.
 
In absense of any other information, I am assuming my original thoughts are the only plausible explaination as to why: To achieve both a gain factor of up to 6 (and it could easlily be 6 if the programmer wasn't stupid) on attack packets, and add a level of obscurity.

---

### Post by Ms. Daisy on 2012-04-01
Doug, have you caught the packets on wireshark or some other network monitor?

---

### Post by Doug S on 2012-04-01
Hi Ms. Daisy, (and congrats on your Ubuntu membership).
 
I use tcpdump (it is just my preference over tshark, nothing more). For realtime stuff, I do sometimes use a windows version of wireshark driven from tcpdump via a reverse ssh tunnel (I only run server ubuntu, no GUI).
 
I always have two tcpdump sessions running, one on my internal NIC and one on my external NIC. The sessions write to files and change files automatically every 10 minutes. Mostly, I don't look at the files, but in the event of what I think might be a security related issue I do. I have heavy internal traffic on ports 22 and 445, so I don't monitor them. Example commands:
 
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600
sudo tcpdump -i eth0 not port 22 and not port 139 and not port 445 -w 'eth0-%F-%H-%M-%S.bin' -G 600
 
For the particular issue of this thread, I added an iptables rule to log each new port 80 TCP connection. When I see that count go up dramatically (at least for my site it is dramatic because my site has an extremely low hit rate) I investigate.

---

### Post by matt_symes on 2012-04-01
> **Doug S said:**
> Hi Ms. Daisy, (and congrats on your Ubuntu membership).
 
I use tcpdump (it is just my preference over tshark, nothing more). For realtime stuff, I do sometimes use a windows version of wireshark driven from tcpdump via a reverse ssh tunnel (I only run server ubuntu, no GUI).
 
I always have two tcpdump sessions running, one on my internal NIC and one on my external NIC. The sessions write to files and change files automatically every 10 minutes. Mostly, I don't look at the files, but in the event of what I think might be a security related issue I do. I have heavy internal traffic on ports 22 and 445, so I don't monitor them. Example commands:
 
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600
sudo tcpdump -i eth0 not port 22 and not port 139 and not port 445 -w 'eth0-%F-%H-%M-%S.bin' -G 600
 
For the particular issue of this thread, I added an iptables rule to log each new port 80 TCP connection. When I see that count go up dramatically (at least for my site it is dramatic because my site has an extremely low hit rate) I investigate.

Well you have at least one new connection as i just checked out your web site :D

---

### Post by webservervideos on 2012-04-02
those packets or returns or that get sent to the ipaddress from your server are usually part of a dedicated attempt to do a denial of service attack.

might only be 6 times on your server, but if they do that to 1 million servers that is 6 million little packets flooding that server with that ip.

if I read your stuff right.

best thing to do is find a way to not respond at all when something calls about that ip address.

---

### Post by Doug S on 2012-04-03
Yes, exactly. The real attacker gets (or can get, this one was a bit daft) 6X gain on their maximum outgoing packet rate.
By the way, I did have a temporary iptables rule to identify this stuff and then drop all packets thereafter. I removed the rule sometime ago. I could not do the rule based on source or destination IP address, because that was not a constant (well, it was constant per event, but I wanted a generic rule). I based my rule on port 0, which was unique to this signature. For the previous [signature of 2010.02 ]("http://www.smythies.com/~doug/network/syn2011.02/index.html")there was a unique window size on which to base an iptables rule.
 
The signature of this one was different than I have seen before. I saw some brief experiments with this particular signature for about a month before the real attempts. It was shortlived covering a couple of weeks only. I have not seen it since, but like I mentioned in the original posting, I find these type of events extremely rare.

---

### Post by dontquoteme on 2012-04-05
> **Doug S said:**
> 
I was just wondering if anyone elese has an opinion as to what its purpose might be.

You asked for an opinion as to a purpose of such light scanning.

Could this be reconnaissance to locate a zombie printer or idle dumb device - that's trusted inside your network?
This attack needs to be done on the sly.  One Syn.  As you say, the devices respond.. and the Sequence is the only thing I could think of that they'd be looking for that would be available to them if they're using spoofed IP's.
This would tell them if they've hit the jackpot.  An idle Zombie that is trusted within your network.

Great question by the way. :)

[https://en.wikipedia.org/wiki/Idle_scan](https://en.wikipedia.org/wiki/Idle_scan)

---

### Post by Doug S on 2012-04-06
> You asked for an opinion as to a purpose of such light scanning.
I did, and I thank you for your reply/suggestion and for the link you edited in.
That link is pretty interesting. If I read it correctly, then I should have seen the occasional TCP RST packet coming back from the zombie computer... Going back and re-examing the tcpdump data... Oh!!! look what I found:```
doug@doug-64:~/tcpdump/040$ grep -v "Flags \[S\]" 96_i.txt
2012-02-20 18:14:40.903509 IP 96.55.202.167.103 > 209.121.28.192.80: Flags [R], seq 6750209, win 0, length 0
2012-02-20 18:17:13.310355 IP 96.55.202.167.16426 > 209.121.28.192.80: Flags [R], seq 1076494337, win 0, length 0
``` I had previously missed those two "different" packets. I have often thought that sometimes with this stuff, the real story is hidden somewhere within an overwhelming number of packets.
 
I think I will go back and have another look at some of the other cases, including the much bigger event from a year ago. I'll report back here, perhaps in a couple of days, if I find anything more.

---

### Post by dontquoteme on 2012-04-06
> **Doug S said:**
> 
 
I think I will go back and have another look at some of the other cases, including the much bigger event from a year ago. I'll report back here, perhaps in a couple of days, if I find anything more.

Yay! Great find! 

Fyodor is the guru on Zombie scans.  
[http://nmap.org/book/idlescan.html](http://nmap.org/book/idlescan.html)

Idle scanning can sometimes be used to map out these trust relationships. The key factor is that idle scan results list open ports from the zombie host's perspective. A normal scan against the aforementioned database server might show no ports open, but performing an idle scan while using the web server's IP as the zombie could expose the trust relationship by showing the database-related service ports as open.
Mapping out these trust relationships can be very useful to attackers for prioritising targets.

This is the most stealthy scan that I'm aware of... Only the RST's exist - as a give away that they're monitoring your Sequence ID's.

Very intriguing question. :)

---

### Post by Doug S on 2012-04-07
O.K. what I found out by going back and looking again:
 
First, the [older event ]("http://www.smythies.com/~doug/network/syn2011.02/index.html")of a year ago: 18617 incoming packets, no RST packet; Sequence number always the same; Window size unique and always the same; Source ports look normal. I am still of the opinion the objective of this one was the packet gain factor previoulsy discussed.
 
Second, the more recent event, that led to this thread:
 
While I don't think I can prove it definately either way, I now think these were actually attacks with my server being the target. However, RST packets are rare. I think the purpose was to determine if my server had an older kernel perhaps vulnerable to TCP sequence number prediction. The incoming packet sequence numbers were always the port number * 65536. There was a high degree of preference for port numbers in binary to be simple sequences, with 1 or 2 or no bits set. Here is a partial histogram of source ports used for one event (35 174.103.219.11.232 means source port 232 of source IP 174.103.219.11 occured 35 times):>  35 174.103.219.11.232
42 174.103.219.11.144
43 174.103.219.11.16
43 174.103.219.11.48
47 174.103.219.11.208
49 174.103.219.11.112
51 174.103.219.11.176
74 174.103.219.11.240
89 174.103.219.11.224
92 174.103.219.11.160
94 174.103.219.11.32
112 174.103.219.11.96
190 174.103.219.11.192
193 174.103.219.11.64
378 174.103.219.11.0
378 174.103.219.11.128
According to an RFC reference I found, the reply initial TCP sequence number might be a function of, among other things, the source port and IP address.
Event summaries:
 
Event 1: Begin 2012.02.12 12:12:04.361232 End: 2012.02.13 04:42:56.437905
IP Address: 174.103.219.11 win 65535 seq=65536*port
RST packets: No. Port 0: 378 Packets
Incoming packets: 6307 Outgoing packets: 23509 Total packets: 29816 Gain ratio: 3.727
 
Event 2: Begin 2012.02.13 05:17:55.323350 End: 2012.02.13 08:15:37.457917
IP Address: 75.87.211.76 win 65535 seq=65536*port
RST packets: No. Port 0: 143 Packets
Incoming packets: 2471 Outgoing packets: 8609 Total packets: 11080 Gain ratio: 3.484
 
Event 3: Begin 2012.02.13 11:43:50.023450 End: 2012.02.13 17:37:10.407913
IP Address: 90.223.205.138 win 65535 seq=65536*port
RST packets: Yes, 1. Port 0: 259 Packets
Incoming packets: 4319 Outgoing packets: 16930 Total packets: 21249 Gain ratio: 3.920```
2012-02-13 13:52:13.106081 IP 90.223.205.138.28867 > 209.121.28.192.80: Flags [R], seq 1891827713, win 0, length 0
```Event 4: Begin 2012.02.20 18:10:15.578726 End: 2012.02.20 20:52:36.157903
IP Address: 96.55.202.167 win 65535 seq=65536*port
RST packets: Yes, 2. Port 0: 150 Packets
Incoming packets: 2680 Outgoing packets: 7082 Total packets: 9762 Gain ratio: 3.6425```
2012-02-20 18:14:40.903509 IP 96.55.202.167.103 > 209.121.28.192.80: Flags [R], seq 6750209, win 0, length 0
2012-02-20 18:17:13.310355 IP 96.55.202.167.16426 > 209.121.28.192.80: Flags [R], seq 1076494337, win 0, length 0
```References:
[http://www.securityfocus.com/bid/49289/info](http://www.securityfocus.com/bid/49289/info) 
[http://www.ietf.org/rfc/rfc1948.txt](http://www.ietf.org/rfc/rfc1948.txt) 
[http://tools.ietf.org/id/draft-ietf-tcpm-rfc1948bis-01.txt](http://tools.ietf.org/id/draft-ietf-tcpm-rfc1948bis-01.txt)

---

### Post by BigCityCat on 2012-04-07
I really don't know much about what you guys are talking about but I had read an article and was wondering if this could be related.

[http://arstechnica.com/business/news/2012/01/new-slow-motion-dos-attack-just-a-few-pcs-little-fear-of-detection.ars](http://arstechnica.com/business/news/2012/01/new-slow-motion-dos-attack-just-a-few-pcs-little-fear-of-detection.ars)

---

### Post by sammiev on 2012-04-07
> **BigCityCat said:**
> I really don't know much about what you guys are talking about but I had read an article and was wondering if this could be related.

[http://arstechnica.com/business/news/2012/01/new-slow-motion-dos-attack-just-a-few-pcs-little-fear-of-detection.ars](http://arstechnica.com/business/news/2012/01/new-slow-motion-dos-attack-just-a-few-pcs-little-fear-of-detection.ars)

Thanks for the great read.

---

### Post by dontquoteme on 2012-04-08
*Smiles*

A RST is to use the system against itself.  The Art of War - always use the resources of the system against itself.

You've no doubt closed down ping etc.  But if the attacker can trigger a RST - then by default they know "something" is there!!  Bet the IETF never thought of RST being used by attackers.   I thought that was a great use of the RST, though naughty.


As for source ports... *laughs*  They're testing if you've taken any shortcuts.

           --source-port *<portnumber>*;           -g *<portnumber>* (Spoof source port number)                                          One surprisingly common misconfiguration is to trust traffic based only on the source port number.  It is easy to understand how this comes about.  An administrator will set up a shiny new firewall, only to be flooded with complaints from ungrateful users whose applications stopped working.  In particular, DNS may be broken because the UDP DNS replies from external servers can no longer enter the network.  FTP is another common example.  In active FTP transfers, the remote server tries to establish a connection back to the client to transfer the requested file.
Secure solutions to these problems exist, often in the form of application-level proxies or protocol-parsing firewall modules. Unfortunately there are also easier, insecure solutions.  Noting that DNS replies come from port 53 and active FTP from port 20, many administrators have fallen into the trap of simply allowing incoming traffic from those ports.  They often assume that no attacker would notice and exploit such firewall holes.  In other cases, administrators consider this a short-term stop-gap measure until they can implement a more secure solution.  Then they forget the security upgrade. 
Overworked network administrators are not the only ones to fall into this trap.  Numerous products have shipped with these insecure rules.  Even Microsoft has been guilty.  The IPsec filters that shipped with Windows 2000 and Windows XP contain an implicit rule that allows all TCP or UDP traffic from port 88 (Kerberos).  In another well-known case, versions of the Zone Alarm personal firewall up to 2.1.25 allowed any incoming UDP packets with the source port 53 (DNS) or 67 (DHCP).


Sequence numbers are critical for a man in the middle attack!  Soft scanning for sequence numbers would imply hijacking...  they are motivated to jump into an already authenticated session and bypass any password cracking.  Looking at the motive or end game of an attacker can help understand what you can see.  Only you know the value of data being protected... if it's valuable then you can expect sessions to be hijacked with predictable TCP sequencing.  Luckily you've already blocked that avenue.. so all's well that ends well. :)

I have enjoyed this thread.  A Giant *thanks*.

---

### Post by dontquoteme on 2012-04-08
There was a high degree of preference for port numbers in binary  to be simple sequences.
********

I'm not sure if I've understood what you meant by binary sequence here... so dug up the algorithms behind the Zombie Scan.... 

**Zombie Scan Implementation Algorithm.**

Parallelism is tricker than with other scan techniques - scans a max of 100 ports at a time.
The number of IP ID increments will expose how many target ports are open.
If probes find zombie IP ID has increased x times, there must be x open ports.
**It finds the open ports with a binary search.**

Woohoo... the Zombie algorithm uses a binary search!! (It doesn't when Parallelism isn't in action).
It's splitting a group into 2 and separately sending probes to each subgroup.  If a subgroup shows open ports, it's divided again - and continues until those ports are identified.

non random binary sequences?? Caused by the algorithm of the Zombie scan...in a certain mode.  I hope that's what you can see. :)

---

### Post by Doug S on 2012-04-08
> **dontquoteme said:**
> There was a high degree of preference for port numbers in binary to be simple sequences.
********
 
I'm not sure if I've understood what you meant by binary sequence here... so dug up the algorithms behind the Zombie Scan....
 
I only meant that the source port numbers were mostly extremely simple, when observed in binary. Note that the destination port number was always, for every event, port 80.
 
> There was a high degree of preference for port numbers in binary to be simple sequences, with 1 or 2 or no bits set. Here is a partial histogram of source ports used for one event (35 174.103.219.11.232 means source port 232 of source IP 174.103.219.11 occured 35 times):Hopefully for added clarity, I'll repost the same histogram with the source port also listed in binary. Notice the most significant 8 bits are always 0, and the least significant 4 bits are always 0 (until we get down to the 35 occurences case):```
35 174.103.219.11.232  00000000 11101000
42 174.103.219.11.144  00000000 10010000
43 174.103.219.11.16   00000000 00010000
43 174.103.219.11.48   00000000 00110000
47 174.103.219.11.208  00000000 11010000
49 174.103.219.11.112  00000000 01110000
51 174.103.219.11.176  00000000 10110000
74 174.103.219.11.240  00000000 11110000
89 174.103.219.11.224  00000000 11100000
92 174.103.219.11.160  00000000 10100000
94 174.103.219.11.32   00000000 00100000
112 174.103.219.11.96  00000000 01100000
190 174.103.219.11.192 00000000 11000000
193 174.103.219.11.64  00000000 01000000
378 174.103.219.11.0   00000000 00000000
378 174.103.219.11.128 00000000 10000000
```

---

