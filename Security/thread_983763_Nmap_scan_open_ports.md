---
title: "Nmap scan open ports"
date: 2008-11-16
forum: Security
---

### Post by lovinglinux on 2008-11-16
I used [[COLOR="DarkRed"]**nmap-online**[/COLOR]]("http://nmap-online.com") to scan my machine, which is behind a router, currently with no ports forwarded.

This is the result:

```
Nmap Options: -p1-5000 -T4

Not shown: 4998 filtered ports
PORT STATE SERVICE
53/tcp open domain
80/tcp open http
```

I have the following iptables rules related to those ports:

INPUT
```
iptables -A INPUT -i eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 53 -s xxx.xxx.x.xx -j ACCEPT 
iptables -A INPUT -i eth0 -p udp -m udp --sport 53 -s xxx.xxx.x.xx -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 53 -s yyy.yyy.y.yy -j ACCEPT
iptables -A INPUT -i eth0 -p udp -m udp --sport 53 -s yyy.yyy.y.yy -j ACCEPT
```

OUTPUT
```
iptables -A OUTPUT -o eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -d xxx.xxx.x.xx -j ACCEPT 
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -d xxx.xxx.x.xx -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -d yyy.yyy.y.yy -j ACCEPT 
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -d yyy.yyy.y.yy -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -s 192.168.x.x -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 80 -s 192.168.x.x -j ACCEPT
```

*[SIZE="2"]Note: xxx.xxx.x.xx and yyy.yyy.y.yy are the DNS servers of my ISP.[/SIZE]*

So, why I still get ports 53 and 80 as opened? Is it due to nmap-online scanning my computer from the same IP of their web site and my INPUT rule "--state ESTABLISHED,RELATED"?

If I delete the ESTABLISHED state for nmap-online IP (using IPTState) just after hitting the "Scan Now" button I get this result:

```
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.47 seconds
```

When I scan my computer using [[COLOR="DarkRed"]**PC Flank**[/COLOR]]("http://www.pcflank.com/scanner1.htm") service, which I guess use a different IP for scanning, the result give me "Stealth" for both ports.

The output of **sudo netstat -plntu** do not show any services listening to any ports.

Is this something I should be concerned about? Should I change my iptables rules?

---

### Post by cariboo on 2008-11-16
As you said in your post you are behind a router and you have no ports forwarded. The open ports you are seeing are on your router. Trying to get the firewall on your computer to block those port is not going to work. You more then likely have remote access set to active and port 53 has to do with the dns server. You will have to close those ports from the router management console.

Edit: I had another look at the scan, it almost looks like the online scanner is seeing my ISP's server, which makes sense, as it has to have the listed ports open. I am able to do a scan of my own external ip address and I get these results using the same switches:

```
sudo nmap -F -T5 -sS 70.77.129.14

Starting Nmap 4.62 ( http://nmap.org ) at 2008-11-16 12:42 PST
Interesting ports on S01060018395078d5.ca.shawcable.net (70.77.129.14):
Not shown: 1275 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 2.725 seconds
```

Jim

---

### Post by lovinglinux on 2008-11-16
> **cariboo907 said:**
> As you said in your post you are behind a router and you have no ports forwarded. The open ports you are seeing are on your router. Trying to get the firewall on your computer to block those port is not going to work. You more then likely have remote access set to active and port 53 has to do with the dns server. You will have to close those ports from the router management console


Remote access in the router is not active, that's for sure. 

I don't get it. If my iptables rules allow input/output on port 53 only from/to my ISP DNS, why the scanner is seeing it as open? Let's assume the router is letting everything pass through, the scanner shouldn't see the port as open because of the iptables settings.

For example, if I scan the port 49152 without opening it in the router, then I get this result:

nmap-online
```
49152/tcp filtered unknown
```

PC Flank
```
49152  	   	stealthed  	     	n/a  	     	n/a
```
	
And nothing shows up in the iptables blocked log, because the connections are not passing through the router.

If I open the port in the router, but don't ACCEPT connections on that port in the iptables, then I get the same result:

nmap-online
```
49152/tcp filtered unknown
```

PC Flank
```
49152  	   	stealthed  	     	n/a  	     	n/a
```

But the SYN connections from the scanner shows up in the iptables blocked log. So the connection attempt is passing through the router, but not through the iptables.

Then, if I add an iptables rule to ACCEPT connections on port 49152 I get the same result from nmap, but PC Flank result is blank:

```
49152/tcp filtered unknown
```

Nothing appears in the iptables blocked log because the rule is allowing connections in that port, but the scanner cannot connect because there isn't any service listening on that port.

Then if start a service that listen to that port, I get these results.

nmap-online
```

49152/tcp filtered unknown
```

PC Flank
```
49152  	   	open  	     	n/a  	     	n/a
```

PC Flank result makes sense to me, but I can't understand nmap results.

If I remove the "ESTABLISHED, RELATED" rules I can't access any web site, because the web site ACK SYN replies can't get through the firewall, so this rules is indeed necessary.

So I don't understand why I'm getting nmap results with ports 80 and 53 opened.

---

### Post by kevdog on 2008-11-16
are you scanning localhost, 127.0.0.1, your LAN IP address, or WAN IP address?

---

### Post by lovinglinux on 2008-11-17
> **kevdog said:**
> are you scanning localhost, 127.0.0.1, your LAN IP address, or WAN IP address?

I'm scanning my external IP. It is detected by both services when I visit their pages.

---

### Post by kevdog on 2008-11-17
So not to beat a dead horse, however if you are scanning your external IP, aren't you just scanning the ports open on your router?

I think this may have been mentioned above -- or maybe that is what you want?

---

### Post by lovinglinux on 2008-11-17
> **kevdog said:**
> So not to beat a dead horse, however if you are scanning your external IP, aren't you just scanning the ports open on your router?

As long as I understand, those services will scan the ports on my router, but if a port is forwarded, then they will reach my machine iptables. If my machine iptables are allowing traffic on that port, then they will reach any listening service on the machine.

The result's of PC Flank scan corroborate this.

Closed port on router = [COLOR="Lime"]**stealth**[/COLOR]
Open port on router + DROP on iptables = [COLOR="Lime"]**stealth**[/COLOR]
Open port on router + REJECT on iptables = [COLOR="RoyalBlue"]**closed**[/COLOR]
Open port on router + ACCEPT on iptables = [COLOR="Red"]**open**[/COLOR]

What I don't understand is why nmap-online flags ports 80 and 53 as open and why I get the following results:

Closed port on router =  [COLOR="DarkRed"]**filtered unknown**[/COLOR]
Open port on router + DROP on iptables = [COLOR="DarkRed"]**filtered unknown**[/COLOR]
Open port on router + REJECT on iptables = *
Open port on router + ACCEPT on iptables =  [COLOR="DarkRed"]**filtered unknown**[/COLOR]

* *didn't tested and need to wait 24 hours to make another scan*

---

### Post by kevdog on 2008-11-17
What do you get if you use nmap to scan your LAN IP address?  Same results?

---

### Post by lovinglinux on 2008-11-17
> **kevdog said:**
> What do you get if you use nmap to scan your LAN IP address?  Same results?

I assume I have to run nmap from my machine for this, right? If I scan my own internal IP I get all ports closed and if I scan the router IP I get port 80 open.

---

### Post by buyyourall4 on 2008-11-17
[size=5][color=black]it is a windows operation system  [/color][/size][[size=5][color=black]chinese mobile phone[/color][/size]](http://www.buyyourall.com/)[size=5][color=black] , it makes people think of S1 of dopoda, just as the picture. Yes  the out-look is like dopoda S1 exactly, but the function is over S1 since it has wifi function. yet what amazy you is it`s low price, not over than 200USD, can you believe?  it is trueth.[/color][/size][size=5]now the request is over the offer, lots of orders from worldwide keep the factory busy in the manufacture without stop day and night.would you like the details? click the picture please.[/size][[img]http://www.buyyourall.com/syssite/home/shop/1/pictures/productsimg/big/1042.jpg[/img][size=5][color=sandybrown][/color][/size]](http://www.buyyourall.com)

---

### Post by kevdog on 2008-11-18
So I can't explain your results. 

If you have blocked everything with iptables on the machine in question, and use nmap to scan all ports from the machine -- to the machine -- that should be your answer.

Obviously your router or your ISP is messing something up when you scan from external address.

---

### Post by lovinglinux on 2008-11-18
> **kevdog said:**
> So I can't explain your results. 

If you have blocked everything with iptables on the machine in question, and use nmap to scan all ports from the machine -- to the machine -- that should be your answer.

Obviously your router or your ISP is messing something up when you scan from external address.

Thanks for trying.

Could be possible that nmap-online is giving me wrong results?

---

### Post by kevdog on 2008-11-18
No, but its possible you are scanning a box that you are not expecting or predicting.

---

### Post by Kinstonian on 2008-11-18
That's definitely scanning your router.  There isn't really anything I know of you can do other than from a remote computer-- 

1.  Using the -V option on nmap to get more information on what's listening on TCP/80.

2.  Telneting or using a browser to connect to your router's external IP on port 80 and see for yourself what (if anything) you get back.

---

### Post by lovinglinux on 2008-11-20
Today all results from nmap gives me that all 5000 ports scanned are filtered and I didn't changed any configuration in the router. Go figure.

---

