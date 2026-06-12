---
title: "Strange Incoming Probes"
date: 2011-05-05
forum: Security
---

### Post by SparTacux on 2011-05-05
I first made this post in the General Help section but it soon got lost in a myriad of other posts. I hope the Forum admins don't mind me moving it here as it's more likely to be solved here.

Weird one this.

Quite often when I first power up my modem router ( NETGEAR DG834GT ) my router logs show my modem being bombarded with incoming traffic from a variety of sources but strangely they are aimed at the same port. Today the port being probed is UDP /TCP port 28776. My modem router sends its logs on port 514 ( SYSLOG ) to my laptop. On the laptop I can view the live traffic from any computer on my network by running System Log Viewer and opening the modem log file I created. Using fixed IP addresses for each computer I can see what traffic comes from any particular PC.

As I stated, my modem router is 'often' bombarded with traffic aimed at just one port but from many different sources & as yet I am unable to work out the reason for it. I thought I'd chuck it up here to see what you guys come up with.

In the example below you can see my router come on then Immediately I get the probes. These probes to port 28776 went on for an hour or so until I decided to reboot the router and pick up a new IP address. I had the same thing happen yesterday except the port was port 51858.

Could this be  a router firmware problem? Other possibilities that come  to mind are some kind of decoy attack or an attempt to flood my syslog  system.

Extra notes:
Only two computers are in use here. One is running Linux Mint from a Live USB and the other is my laptop collecting the log details & running Ubuntu 9.10. None are accessing the internet & the only packets that leave the computers are DNS calls to get the IP's for the  NTP servers.  

Any ideas?

May 5 17:34:24 Initialize LCP.
May 5 17:34:24 LCP is allowed to come up.
May 5 17:34:24 CHAP authentication success
May 5 17:34:24 UDP Packet - Source:87.202.138.226,21145 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 TCP Packet - Source:92.3.185.48,51430 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 TCP Packet - Source:68.151.45.235,54285 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:89.137.118.9,15921 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 TCP Packet - Source:46.189.164.12,59922 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:79.142.59.234,64781 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:89.136.45.92,62594 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 Send out NTP request to 91.189.94.4
May 5 17:34:24 Receive NTP Reply from 91.189.94.4
May 5 17:34:24 UDP Packet - Source:89.101.179.38,60881 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:201.243.182.132,33075 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:86.80.111.240,6480 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:188.107.8.76,50955 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:79.164.46.236,14521 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:201.243.182.132,33075 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:87.202.138.226,21145 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:113.17.161.207,2668 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 TCP Packet - Source:68.151.45.235,54285 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.236,58251 Destination:194.72.6.57,53 - [DNS rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.236,41848 Destination:194.72.6.57,53 - [DNS rule match]
May 5 17:34:24 UDP Packet - Source:81.233.219.51,13514 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [NTP rule not match]
May 5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [OUTBLOCKU rule match]
May 5 17:34:24 UDP Packet - Source:89.137.118.9,15921 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:113.17.161.207,2668 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:201.243.182.132,33075 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:89.136.45.92,62594 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:89.101.179.38,60881 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [NTP rule not match]
May 5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [OUTBLOCKU rule match]
May 5 17:34:24 UDP Packet - Source:90.151.184.175,49803 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:71.105.182.236,60356 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.231,58704 Destination:194.73.82.242,53 - [DNS rule match]
May 5 17:34:24 UDP Packet - Source:92.113.119.220,48389 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.231,123 Destination:91.189.94.4,123 - [NTP rule match]
May 5 17:34:24 UDP Packet - Source:192.168.0.231,43753 Destination:194.72.6.57,53 - [DNS rule match]
May 5 17:34:24 UDP Packet - Source:87.221.28.17,14510 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 TCP Packet - Source:85.167.42.13,20019 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:139.142.163.26,5321 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May 5 17:34:24 UDP Packet - Source:91.103.79.47,20855 Destination: x.x.248.106,28776 - [INBLOCK rule match]

---

### Post by lloyd_b on 2011-05-06
What it looks like is that a previous user of that IP address was part of a P2P network such as Gnutella (used by Limewire and others).  While they held that address, the IP/port combination they were using was propagated through that network.

Many such P2P clients routinely randomize the ports they use, to make it more difficult for ISPs to block such traffic.

Once they disconnected, and you picked up that IP, nodes on that network were still trying to connect to that node using that IP/port combination, and you were receiving (and blocking) the connection attempts.

If the volume of those requests isn't enough to interfere with your use of the network, then I'd just ignore them.  If the volume *is* enough to cause problems, then I'd suggest rebooting and picking up a new IP - depending on what that other person was doing, it could literally be *days* before the traffic drops off (for instance, if they're in the cache of a large number of nodes as having a very popular file available for download).

Lloyd B.

---

### Post by Baumbart on 2011-05-06
I have no clue what it is but I really wouldn't ignore it for one reason:
When I yahoo 'tcp "port 28776" I almost exclusively get some chinese stuff with the sentence "IE IFRAME html tag buffer overflow vulnerability which binds a shell to **tcp** **port 28776**"
see [here]("http://de.search.yahoo.com/search;_ylt=A7x9QXknjsNNwUQAClwzCQx.?p=tcp+%22port+28776%22&fr2=sb-top&fr=yfp-t-708&rd=r1")

That's not necessarily connected with your problem but if I were you I'd want to know what is going on.

Do you know if there is something actually listening to that port?

EDIT: You might be interested in [this site]("http://isc.incidents.org/port.html?port=28776") too. don't know if it is really useful.
The whois search there for your source IPs shows a whole bunch of telecomunication institutions.
The "Latin American and Caribbean IP address Regional Registry" for instance and such stuff.
Again, I don't know if that means something.

---

### Post by 3rdalbum on 2011-05-06
The incoming connections are being blocked, so there's nothing to worry about unless it's slowing down your internet. These might be computers looking for specific vulnerabilities to infect your computer (it won't find those vulnerabilities, because your firewall is blocking the connections); or it might be otherwise innocent connections (some IRC servers do port probing to prevent botnets from getting commands from within IRC channels).

In short, they're being blocked, so don't worry.

---

### Post by Baumbart on 2011-05-06
> **3rdalbum said:**
> These might be computers looking for specific vulnerabilities to infect your computer (it won't find those vulnerabilities, because your firewall is blocking the connections); or it might be otherwise innocent connections (some IRC servers do port probing to prevent botnets from getting commands from within IRC channels).

When and why is something like that happening?
Do they randomly scan IPs or is there something the user has done to get that sort of attention?

---

### Post by 3rdalbum on 2011-05-06
> **Baumbart said:**
> When and why is something like that happening?
Do they randomly scan IPs or is there something the user has done to get that sort of attention?

It's random. It happens to everybody at all times, but most people don't notice it because either their firewall doesn't send logs, or they don't have a firewall so it never gets logged. It happens because virus writers are nasty people.

If you've ever heard that an unpatched Windows XP gets viruses within 5 minutes, it's because of this constant vulnerability-scanning done by already-infected computers.

---

### Post by SparTacux on 2011-05-06
> **lloyd_b said:**
> What it looks like is that a previous user of that IP address was part of a P2P network such as Gnutella (used by Limewire and others).  While they held that address, the IP/port combination they were using was propagated through that network.

Many such P2P clients routinely randomize the ports they use, to make it more difficult for ISPs to block such traffic.

Once they disconnected, and you picked up that IP, nodes on that network were still trying to connect to that node using that IP/port combination, and you were receiving (and blocking) the connection attempts.

If the volume of those requests isn't enough to interfere with your use of the network, then I'd just ignore them.  If the volume *is* enough to cause problems, then I'd suggest rebooting and picking up a new IP - depending on what that other person was doing, it could literally be *days* before the traffic drops off (for instance, if they're in the cache of a large number of nodes as having a very popular file available for download).

Lloyd B.

That sounds plausible - my only concern is the frequency of it happening. 

I'm guessing there are 65,536 IP addresses that can be assigned by my ISP to customers in my geographical area. How many of them would be affected by this problem on turning on the modem like I am? I typically get something  like three of these events each week. It doesn't seem to affect my network enough to notice a difference in speed, etc. The real downside to this is that my log files can get pretty huge as a result of logging all that traffic.  Another downside is that I am using the laptop to observe all my outgoing traffic and all the incoming crap really interferes with that process.

I do tend to reboot the modem when I see it happening. It just seems I'm rebooting the router once too often. 
 
Cheers

---

### Post by SparTacux on 2011-05-06
> **Baumbart said:**
> I have no clue what it is but I really wouldn't ignore it for one reason:
When I yahoo 'tcp "port 28776" I almost exclusively get some chinese stuff with the sentence "IE IFRAME html tag buffer overflow vulnerability which binds a shell to **tcp** **port 28776**"
see [here]("http://de.search.yahoo.com/search;_ylt=A7x9QXknjsNNwUQAClwzCQx.?p=tcp+%22port+28776%22&fr2=sb-top&fr=yfp-t-708&rd=r1")

That's not necessarily connected with your problem but if I were you I'd want to know what is going on.

Do you know if there is something actually listening to that port?

EDIT: You might be interested in [this site]("http://isc.incidents.org/port.html?port=28776") too. don't know if it is really useful.
The whois search there for your source IPs shows a whole bunch of telecomunication institutions.
The "Latin American and Caribbean IP address Regional Registry" for instance and such stuff.
Again, I don't know if that means something.

Port 28776 was the port being probed yesterday. On other occasions it's another strange port and then another one, etc. The ports in question are usually non standard but the incoming traffic stays fixed to that one port. I've done the whois on the source IP's and they come from all over the world yet all are  aimed at the one port on my system.  There's nothing listening on those ports and the traffic does get blocked by my modem firewall.

---

### Post by SparTacux on 2011-05-06
> **Baumbart said:**
> When and why is something like that happening?
Do they randomly scan IPs or is there something the user has done to get that sort of attention?

It's funny you guys should mention that ;-)

I've not used IRC or any chat in years but tried it out the other day. I did get a through probing too on quite a few ports. Take a look at the logs: This log below isn't complete either- a **** load of ports were probed other than the ones listed below & the process continued for some time.



```
Apr 21 16:33:04 UDP Packet - Source:192.168.0.230,33180 Destination:194.72.6.57,53 - [DNS rule match]
Apr 21 16:33:04 UDP Packet - Source:192.168.0.230,41921 Destination:194.72.6.57,53 - [DNS rule match]
Apr 21 16:33:04 UDP Packet - Source:192.168.0.230,45449 Destination:194.72.6.57,53 - [DNS rule match]
Apr 21 16:33:04 TCP Packet - Source:192.168.0.230,54176 Destination:217.172.177.133,6667 - [IRC rule match]
Apr 21 16:33:04 TCP Packet - Source:217.172.177.133,45675 Destination: x.x.105.94,113 - [INBLOCK rule match]
Apr 21 16:33:04 TCP Packet - Source:192.168.0.230,54176 Destination:217.172.177.133,6667 - [IRC rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,37361 Destination: x.x.105.94,4480 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,35902 Destination: x.x.105.94,5490 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,42454 Destination: x.x.105.94,80 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36021 Destination: x.x.105.94,3128 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,52997 Destination: x.x.105.94,8090 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36187 Destination: x.x.105.94,8080 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,40661 Destination: x.x.105.94,1039 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,39317 Destination: x.x.105.94,8888 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36154 Destination: x.x.105.94,6669 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,47096 Destination: x.x.105.94,6588 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,48732 Destination: x.x.105.94,808 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,47221 Destination: x.x.105.94,3332 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,43547 Destination: x.x.105.94,443 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,33823 Destination: x.x.105.94,5000 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,41766 Destination: x.x.105.94,1080 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,58057 Destination: x.x.105.94,9000 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,48888 Destination: x.x.105.94,8082 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,54473 Destination: x.x.105.94,6661 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,33112 Destination: x.x.105.94,5800 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,43500 Destination: x.x.105.94,6665 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,58190 Destination: x.x.105.94,5634 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,33124 Destination: x.x.105.94,1050 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,46596 Destination: x.x.105.94,35233 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,50507 Destination: x.x.105.94,19991 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,41833 Destination: x.x.105.94,1098 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,39506 Destination: x.x.105.94,3382 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,45774 Destination: x.x.105.94,6664 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,52168 Destination: x.x.105.94,1200 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,57496 Destination: x.x.105.94,1039 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,49345 Destination: x.x.105.94,443 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,55745 Destination: x.x.105.94,444 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,57809 Destination: x.x.105.94,58 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,42217 Destination: x.x.105.94,40 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,53213 Destination: x.x.105.94,7070 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,51148 Destination: x.x.105.94,9988 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,53798 Destination: x.x.105.94,559 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,43154 Destination: x.x.105.94,1025 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,39846 Destination: x.x.105.94,1979 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,49893 Destination: x.x.105.94,3801 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,41607 Destination: x.x.105.94,2000 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36549 Destination: x.x.105.94,9999 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,51182 Destination: x.x.105.94,24973 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,57693 Destination: x.x.105.94,1039 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,43797 Destination: x.x.105.94,1028 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,34587 Destination: x.x.105.94,1033 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,45721 Destination: x.x.105.94,1027 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,59052 Destination: x.x.105.94,1029 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,38681 Destination: x.x.105.94,443 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,40972 Destination: x.x.105.94,63808 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36540 Destination: x.x.105.94,1030 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,35190 Destination: x.x.105.94,1025 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,46361 Destination: x.x.105.94,9100 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,44776 Destination: x.x.105.94,8020 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,41276 Destination: x.x.105.94,1026 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,38879 Destination: x.x.105.94,1080 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,48739 Destination: x.x.105.94,1234 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,42839 Destination: x.x.105.94,1180 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,34773 Destination: x.x.105.94,1122 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,33559 Destination: x.x.105.94,1200 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,38368 Destination: x.x.105.94,1813 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,45001 Destination: x.x.105.94,3380 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36901 Destination: x.x.105.94,1202 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,46060 Destination: x.x.105.94,3128 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,46886 Destination: x.x.105.94,1098 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,54756 Destination: x.x.105.94,1182 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,41271 Destination: x.x.105.94,6000 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,48631 Destination: x.x.105.94,8009 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,50974 Destination: x.x.105.94,8888 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,50989 Destination: x.x.105.94,4914 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,48630 Destination: x.x.105.94,8080 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,44474 Destination: x.x.105.94,9100 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,55424 Destination: x.x.105.94,9090 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,43464 Destination: x.x.105.94,6969 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,40692 Destination: x.x.105.94,8020 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,53663 Destination: x.x.105.94,4471 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,37114 Destination: x.x.105.94,6561 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,34982 Destination: x.x.105.94,6748 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,41585 Destination: x.x.105.94,8278 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,33474 Destination: x.x.105.94,10080 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,58156 Destination: x.x.105.94,10099 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,47451 Destination: x.x.105.94,9999 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,35914 Destination: x.x.105.94,9988 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,47733 Destination: x.x.105.94,19991 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,56230 Destination: x.x.105.94,18844 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,49111 Destination: x.x.105.94,29992 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,56353 Destination: x.x.105.94,10000 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,42288 Destination: x.x.105.94,10777 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,53860 Destination: x.x.105.94,10130 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,47024 Destination: x.x.105.94,24971 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,45973 Destination: x.x.105.94,3128 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,40636 Destination: x.x.105.94,80 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,37785 Destination: x.x.105.94,8081 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,36396 Destination: x.x.105.94,8089 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,45642 Destination: x.x.105.94,23 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,44804 Destination: x.x.105.94,4480 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,40568 Destination: x.x.105.94,23 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,39873 Destination: x.x.105.94,9090 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,50003 Destination: x.x.105.94,8080 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,54846 Destination: x.x.105.94,808 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,40815 Destination: x.x.105.94,6588 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:109.234.106.53,48320 Destination: x.x.105.94,81 - [INBLOCK rule match]
Apr 21 16:33:06 TCP Packet - Source:192.168.0.230,54176 Destination:217.172.177.133,6667 - [IRC rule match]
Apr 21 16:33:07 TCP Packet - Source:217.172.177.133,45675 Destination: x.x.105.94,113 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,37361 Destination: x.x.105.94,4480 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,42454 Destination: x.x.105.94,80 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36187 Destination: x.x.105.94,8080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36154 Destination: x.x.105.94,6669 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,33823 Destination: x.x.105.94,5000 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,47096 Destination: x.x.105.94,6588 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,47221 Destination: x.x.105.94,3332 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,58057 Destination: x.x.105.94,9000 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,48732 Destination: x.x.105.94,808 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40661 Destination: x.x.105.94,1039 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,52997 Destination: x.x.105.94,8090 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,39317 Destination: x.x.105.94,8888 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,35902 Destination: x.x.105.94,5490 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36021 Destination: x.x.105.94,3128 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,39506 Destination: x.x.105.94,3382 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,54473 Destination: x.x.105.94,6661 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,41833 Destination: x.x.105.94,1098 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,43500 Destination: x.x.105.94,6665 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,55745 Destination: x.x.105.94,444 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,34522 Destination: x.x.105.94,7868 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,57809 Destination: x.x.105.94,58 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,46019 Destination: x.x.105.94,1080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,59769 Destination: x.x.105.94,1978 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,45423 Destination: x.x.105.94,2280 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,41607 Destination: x.x.105.94,2000 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,54954 Destination: x.x.105.94,1234 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,48775 Destination: x.x.105.94,3380 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,38433 Destination: x.x.105.94,4044 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,48966 Destination: x.x.105.94,1066 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,33581 Destination: x.x.105.94,1212 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40746 Destination: x.x.105.94,1182 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,35679 Destination: x.x.105.94,8002 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,34587 Destination: x.x.105.94,1033 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,41887 Destination: x.x.105.94,44548 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36825 Destination: x.x.105.94,10000 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,53043 Destination: x.x.105.94,19991 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,45721 Destination: x.x.105.94,1027 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,39827 Destination: x.x.105.94,12654 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,54540 Destination: x.x.105.94,10099 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,41276 Destination: x.x.105.94,1026 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,57693 Destination: x.x.105.94,1039 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40972 Destination: x.x.105.94,63808 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,38681 Destination: x.x.105.94,443 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,35190 Destination: x.x.105.94,1025 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,55547 Destination: x.x.105.94,41080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,34540 Destination: x.x.105.94,43341 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,59052 Destination: x.x.105.94,1029 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,51209 Destination: x.x.105.94,1075 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,34773 Destination: x.x.105.94,1122 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,42111 Destination: x.x.105.94,11225 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,43797 Destination: x.x.105.94,1028 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36901 Destination: x.x.105.94,1202 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,33559 Destination: x.x.105.94,1200 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,38368 Destination: x.x.105.94,1813 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,49890 Destination: x.x.105.94,58 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,38879 Destination: x.x.105.94,1080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,42839 Destination: x.x.105.94,1180 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,46886 Destination: x.x.105.94,1098 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,54756 Destination: x.x.105.94,1182 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36540 Destination: x.x.105.94,1030 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,54730 Destination: x.x.105.94,1081 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,48631 Destination: x.x.105.94,8009 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,53663 Destination: x.x.105.94,4471 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,50989 Destination: x.x.105.94,4914 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,46060 Destination: x.x.105.94,3128 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,45001 Destination: x.x.105.94,3380 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,50974 Destination: x.x.105.94,8888 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,43464 Destination: x.x.105.94,6969 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,48630 Destination: x.x.105.94,8080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,41271 Destination: x.x.105.94,6000 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,41585 Destination: x.x.105.94,8278 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,37114 Destination: x.x.105.94,6561 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40692 Destination: x.x.105.94,8020 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,34982 Destination: x.x.105.94,6748 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,56353 Destination: x.x.105.94,10000 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,35914 Destination: x.x.105.94,9988 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,55424 Destination: x.x.105.94,9090 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,47451 Destination: x.x.105.94,9999 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,47024 Destination: x.x.105.94,24971 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,42288 Destination: x.x.105.94,10777 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,44474 Destination: x.x.105.94,9100 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,58156 Destination: x.x.105.94,10099 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,34036 Destination: x.x.105.94,17235 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,47733 Destination: x.x.105.94,19991 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,33474 Destination: x.x.105.94,10080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,56230 Destination: x.x.105.94,18844 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,49111 Destination: x.x.105.94,29992 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,39873 Destination: x.x.105.94,9090 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,45973 Destination: x.x.105.94,3128 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,45642 Destination: x.x.105.94,23 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40568 Destination: x.x.105.94,23 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40636 Destination: x.x.105.94,80 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,54846 Destination: x.x.105.94,808 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,50003 Destination: x.x.105.94,8080 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,40815 Destination: x.x.105.94,6588 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,37785 Destination: x.x.105.94,8081 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,44804 Destination: x.x.105.94,4480 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,36396 Destination: x.x.105.94,8089 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:109.234.106.53,48320 Destination: x.x.105.94,81 - [INBLOCK rule match]
Apr 21 16:33:09 TCP Packet - Source:192.168.0.230,54176 Destination:217.172.177.133,6667 - [IRC rule match]
Apr 21 16:33:13 TCP Packet - Source:217.172.177.133,45675 Destination: x.x.105.94,113 - [INBLOCK rule match]
Apr 21 16:33:13 TCP Packet - Source:192.168.0.230,54176 Destination:217.172.177.133,6667 - [IRC rule match]
```

---

### Post by bodhi.zazen on 2011-05-06
"Script kiddies" they are called. The constant barrage of this kind of bad behavior is current start of the art on "the internet".

Do not misjudge them by the term "kiddie" , they can do a lot of harm.

If you are not running any servers these things are harmless. a sql injection can not harm you if you are not running mysql, lol.

If you are running a server, yes you need to learn to secure it. That varies by server.

You can use tools such as psad or snort to monitor this activity if you desire. OSSEC ia another excellent option.

If you are running apache / mysql then yes you need to make sure you are not vulnerable to such attacks or use tools such as mod_security.

Nothing like reading the logs to instill a healthy dose of paranoia.

+1 to the notion that the average, unpatched windows computer is cracked within minutes of hitting the internet. The same is NOT true of an Ubuntu desktop.

---

### Post by SparTacux on 2011-05-06
who's paranoid Bodhi.zazen ;-)  DEFCON 1... Call the President ! Open the missile Silo's , Launch the bombers ....  If you can't work out who it is then blame it on the Chinese :-)

---

### Post by demilord on 2011-05-10
Sorry I hijack this, but will I be safe with a up to date ubuntu 10.10 install .. I don't run any server.. without the ufw enabled. I do have a router 'firewall' without exceptions

---

### Post by The Cog on 2011-05-12
> **demilord said:**
> Sorry I hijack this, but will I be safe with a up to date ubuntu 10.10 install .. I don't run any server.. without the ufw enabled. I do have a router 'firewall' without exceptions

It would be better to start your own thread, but yes, unless you install a service (or enable remote desktop - DON'T do that), then you are safe without a firewall.

Actually, even if you install a service and want it publicly reachable, then you don't need a firewall.

---

### Post by SparTacux on 2011-05-12
> **demilord said:**
> Sorry I hijack this, but will I be safe with a up to date ubuntu 10.10 install .. I don't run any server.. without the ufw enabled. I do have a router 'firewall' without exceptions

Hey - don't let my Firewall logs spook you !
It's usually worse than that ;-)

---

