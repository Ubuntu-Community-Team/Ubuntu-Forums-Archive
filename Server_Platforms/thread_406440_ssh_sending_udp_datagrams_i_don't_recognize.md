---
title: "ssh sending udp datagrams i don't recognize"
date: 2007-04-10
forum: Server Platforms
---

### Post by rgeddes on 2007-04-10
I'm using Ubuntu 6.10 Desktop and keep my system updated automatically w/ the Synaptic Package Manager.  I installed the ssh package (I assume it's openssh) and have been using it for the last 2 weeks... nice package works great.

Yesterday I collected tcpdump data on port 22: 

sudo tcpdump -w tcpdump.log.1 dst port 22

because I was getting quite a few failed logins appearing in /var/log/auth.log  (obviously, someone trying to guess an account password to sneak in).  Actually it wasn't a someone in particular... quite a few people from different parts of the world... I looked up the ip addresses on the whois servers.  

I don't think anyone has guessed an account password on my system.. although I'm not 100% sure... 

I looked at the tcpdump data in wireshark, and found mostly, what I expected... many unsuccessful attempts to establish a tcp ssh session.

However, there where 2 curious udp entries at the beginning of the log... and they both originated from my ip address to 2 different ip addresses.

I punched both destination ip addresses into firefox and one returned a webpage that had a message TSOFT-SERVER.   

I would assume that sshd  would not be sending udp datagrams I don't know about...  could this be some sort of recon data being sent back to its owner from a trojan?

Any help resolving this security question would be greatly appreciated
Rich

---

### Post by MJN on 2007-04-11
Have you got more details of the packets? In particular the destination address and port? They're not DNS reverse-lookups are they?

Mathew

---

### Post by rgeddes on 2007-04-11
I'll be a bit careful not to reveal too much data... 

1st udp datagram:

source: (my ip address):36686               
destination: 84.184.203.250:22
```
$> dig -x 84.184.203.250

; <<>> DiG 9.3.2 <<>> -x 84.184.203.250
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21384
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;250.203.184.84.in-addr.arpa.   IN      PTR

;; ANSWER SECTION:
250.203.184.84.in-addr.arpa. 86400 IN   PTR     p54B8CBFA.dip.t-dialin.net.

;; Query time: 380 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Wed Apr 11 10:54:49 2007
;; MSG SIZE  rcvd: 85
```

t-dialin.net leads to a T-Mobile site in germany
yesterday I punched 84.184.203.250 into firefox and connected to a webpage

today, it looks like a firewall is dropping the connection

```
$> sudo nmap -v -p22,80 -P0 84.184.203.250

Starting Nmap 4.20 ( http://insecure.org ) at 2007-04-11 11:18 EDT
Initiating Parallel DNS resolution of 1 host. at 11:18
Completed Parallel DNS resolution of 1 host. at 11:18, 0.10s elapsed
Initiating SYN Stealth Scan at 11:18
Scanning p54B8CBFA.dip.t-dialin.net (84.184.203.250) [2 ports]
Completed SYN Stealth Scan at 11:18, 3.12s elapsed (2 total ports)
Host p54B8CBFA.dip.t-dialin.net (84.184.203.250) appears to be up ... good.
Interesting ports on p54B8CBFA.dip.t-dialin.net (84.184.203.250):
PORT   STATE    SERVICE
22/tcp filtered ssh
80/tcp filtered http

Nmap finished: 1 IP address (1 host up) scanned in 3.351 seconds
               Raw packets sent: 4 (176B) | Rcvd: 0 (0B)
```

The second upd packet 

source: (my ip address):36686               
destination: 80.108.96.112:22

```
$> dig -x 80.108.96.112

; <<>> DiG 9.3.2 <<>> -x 80.108.96.112
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15302
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;112.96.108.80.in-addr.arpa.    IN      PTR

;; ANSWER SECTION:
112.96.108.80.in-addr.arpa. 86400 IN    PTR     chello080108096112.1.11.vie.surfer.at.

;; Query time: 199 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Wed Apr 11 11:30:38 2007
;; MSG SIZE  rcvd: 95
```


I couldn't get this address to respond yesterday or today... filtered service

What strikes me as odd is that the udp packets get sent out first from my machine and then the intrusion attempts start showing up... like a recon team giving the "all clear" signal for an attack.

No proof, only suspicions.

---

### Post by MJN on 2007-04-11
You don't use PCAnywhere do you?
 
Reason I ask is that according to [http://www.iss.net/security_center/advice/Exploits/Ports/groups/PCanywhere/default.htm](http://www.iss.net/security_center/advice/Exploits/Ports/groups/PCanywhere/default.htm) older versions of it used UDP on port 22 for authentication (thanks to a programming error) and newer versions still maintain this for functionality.
 
However I'm trying to work out the connection here, if this is the case, as to why these packets occur before the attacks.... Not without thinking you do have cause for concern - but then there's always the danger of being over-suspicious in these circumstances! Presumably the addresses (e.g. 84.184.203.250) are not appearing elsewhere in your logs? Specifically, they're not the source of the subsequent attacks (not that their absence means much, but their presence certainly would).
 
Mathew

---

### Post by rgeddes on 2007-04-11
I don't use PCAnywhere... thought that was a windows-only program.

It's true... the ip addresses of the subsequent failed login attempts do not intersect with the initial udp datagram addresses... you may have a point there... however, if I played the dr evil role, and I had 'spies' stationed on someone else's turf, I would make sure my 'spies' could not be traced/correlated  back to any attack vector.  That way the 'spies' can survive countermeasures that look for correlations (based on ip address.. ip addresses can be spoofed, so I've been told). 

I realize that the measure/countermeasure games can go on forever... any out-of-the-ordinary information that crosses your path, especially with ssh, would be greatly appreciated.. 

regards
rich

---

### Post by MJN on 2007-04-11
It does all sound very intriguing and your Dr Evil hat is certainly believable...

Has it happened since? Could it be a one (or rather two!) off?

As you know, port 22 is synonymous with SSH which of course only uses TCP... The UDP traffic is just downright weird, but then so is the use of it by PCAnywhere, and the two together seem more than just coincidence...

Putting my Dr Evil I could believe that a compromised machine could well be made to hunt down other machines, perhaps running PCAnywhere that could be exploited, and that your outgoing UDP is evidence of such. But then you're not seeing it all the time? And you've no other reason to believe your machine is, or has been, compromised?

I don't know what to suggest... as you've probably gathered I'm stabbing in the dark really which is arguably not the most efficient way to reach the answer...

Mathew

---

### Post by rgeddes on 2007-04-11
I think I need to gather more data ...  the tcpdump command has alot of options that I can play with...

to begin, I think I'll start by logging all udp datagrams w/ destination port 22 and see what turns up.

Also, I was thinking,  udp datagrams are much less conspicuous than tcp packets, since there is no session established...  ie no trail... once a udp datagram goes out, that's the end of it, unless it's logged... with tcp, a session is initiated that identifies all packets that belong to the session, and as long as the session is alive, there remains a trail.

I'll post what I find...

---

