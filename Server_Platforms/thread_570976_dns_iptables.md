---
title: "dns iptables"
date: 2007-10-08
forum: Server Platforms
---

### Post by gishaust on 2007-10-08
hi everyone

I have setup bind9 and it works fine. but when I put the firewall it does not work i have opened port 53 and still won't work. 

has anyone got any ideas

thanks 

gishaust

---

### Post by ksudbury on 2007-10-08
What firewall are you using? 

Also you say you opened port 53, you know DNS uses 53 UDP and 53 TCP?

---

### Post by gishaust on 2007-10-09
thankyou did not realise.when I change it. it worked

---

### Post by ksudbury on 2007-10-09
Your welcome :) 


Glad you got it sorted.

---

### Post by gishaust on 2007-10-09
Hello again.

I got up this morning and checked the server and  have found the samething is happening again.
 
I dropped the fire wall and dig myalalla.com and it works.

Then I  flushed the firewall and made sure 53 upd and 53 tcp were setup to accept and it is.  I put up the firewall again and it does not let me dig anything. 

Has any one got any ideas what I can do . To sort this out

gishaust

---

### Post by jonobr on 2007-10-09
any possiblity of doing a wireshark/ethereal trace on your client during a query to see where this is failing and post it here?

---

### Post by gishaust on 2007-10-11
Hi people,

Well here is an interesting point. I realises that bind9 was to heavy for a newbie. So I decide to have a look around for a podcast so that listen to someone explain this too me.

I found a site linux reality. WOW,WOW,WOW!!!! I highly recommend that you have a look, especially if you are a newbie.

However  I found out about a simple dns called dnsmasq so i gave it a try I had the dns setup in 10mins but could not get it to work. Guess what I  dropped the firewall and works straight away.

I have installed tshark (wiresharks terminal equivalant  but don't know how to get it to work! more learning).

Does anyone have any tips on how this works?

Thanks Gishaust

---

### Post by MJN on 2007-10-11
Maybe if you post your iptables ruleset someone will be able to spot where you've gone wrong.

If your service works with no firewall turned on then it's not a DNS issue - merely a firewall configuration one (so don't go jumping between DNS servers!).

Mathew

---

### Post by gishaust on 2007-10-11
Ok this is my firewall can anyone see anything wrong with this. Everything works straight away except DNS

target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
(these ports have been change ssh)
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:122222
(these ports have been change webmin)
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:122222
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
LOG        0    --  anywhere             anywhere            LOG level warning

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere

Gishaust

---

### Post by MJN on 2007-10-11
> **gishaust said:**
> I dropped the fire wall and dig myalalla.com and it works.

And **myalalla.com** is your domain name?

I think we need to take a few steps back here... what is your domain name, what do you mean (exactly) when you say you can't dig the name - any name, or just your own? And where from? Is your name server intended to be connected to the Internet?

Also, post the output of **dig google.com A +trace** and **dig myalalla.com A +trace**

Sorry for the all questions but there's a very real danger we're diving in head first and we don't even know if there's any water in the pool yet, nevermind how deep it is (man, that is one seriously bad analogy!).

Mathew

---

### Post by gishaust on 2007-10-11
Thanks for the reply

I don't mind being asked questions as that allows me to understand

To answers your questions
My domain name is purencool.com 
Yes the name server is to connect to the network so i need it for postfix and other machines behind the nat.
I am dig the from the server through a ssh terminal on the personal network

The following example is me dig google.com A +trace with the firewall down

; <<>> DiG 9.3.4 <<>> google.com A +trace
;; global options:  printcmd
.                       351270  IN      NS      L.ROOT-SERVERS.NET.
.                       351270  IN      NS      M.ROOT-SERVERS.NET.
.                       351270  IN      NS      A.ROOT-SERVERS.NET.
.                       351270  IN      NS      B.ROOT-SERVERS.NET.
.                       351270  IN      NS      C.ROOT-SERVERS.NET.
.                       351270  IN      NS      D.ROOT-SERVERS.NET.
.                       351270  IN      NS      E.ROOT-SERVERS.NET.
.                       351270  IN      NS      F.ROOT-SERVERS.NET.
.                       351270  IN      NS      G.ROOT-SERVERS.NET.
.                       351270  IN      NS      H.ROOT-SERVERS.NET.
.                       351270  IN      NS      I.ROOT-SERVERS.NET.
.                       351270  IN      NS      J.ROOT-SERVERS.NET.
.                       351270  IN      NS      K.ROOT-SERVERS.NET.
;; Received 436 bytes from 127.0.0.1#53(127.0.0.1) in 72 ms

com.                    172800  IN      NS      a.gtld-servers.net.
com.                    172800  IN      NS      b.gtld-servers.net.
com.                    172800  IN      NS      c.gtld-servers.net.
com.                    172800  IN      NS      d.gtld-servers.net.
com.                    172800  IN      NS      e.gtld-servers.net.
com.                    172800  IN      NS      f.gtld-servers.net.
com.                    172800  IN      NS      g.gtld-servers.net.
com.                    172800  IN      NS      h.gtld-servers.net.
com.                    172800  IN      NS      i.gtld-servers.net.
com.                    172800  IN      NS      j.gtld-servers.net.
com.                    172800  IN      NS      k.gtld-servers.net.
com.                    172800  IN      NS      l.gtld-servers.net.
com.                    172800  IN      NS      m.gtld-servers.net.
;; Received 488 bytes from 198.32.64.12#53(L.ROOT-SERVERS.NET) in 247 ms

google.com.             172800  IN      NS      ns1.google.com.
google.com.             172800  IN      NS      ns2.google.com.
google.com.             172800  IN      NS      ns3.google.com.
google.com.             172800  IN      NS      ns4.google.com.
;; Received 164 bytes from 192.5.6.30#53(a.gtld-servers.net) in 309 ms

google.com.             300     IN      A       64.233.167.99
google.com.             300     IN      A       72.14.207.99
google.com.             300     IN      A       64.233.187.99
google.com.             345600  IN      NS      ns1.google.com.
google.com.             345600  IN      NS      ns2.google.com.
google.com.             345600  IN      NS      ns3.google.com.
google.com.             345600  IN      NS      ns4.google.com.
;; Received 212 bytes from 216.239.32.10#53(ns1.google.com) in 228 ms

The next is me dig google.com A +trace with the firewall up

; <<>> DiG 9.3.4 <<>> google.com A +trace
;; global options:  printcmd
;; connection timed out; no servers could be reached

The next trace dig myalalla.com A +trace


;; QUESTION SECTION:
;myalalla.com.                  IN      A

;; AUTHORITY SECTION:
com.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1192145575 1800 900 604800 900

;; Query time: 52 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu Oct 11 19:28:58 2007
;; MSG SIZE  rcvd: 106

$ dig myalalla.com A +trace

; <<>> DiG 9.3.4 <<>> myalalla.com A +trace
;; global options:  printcmd
.                       350626  IN      NS      E.ROOT-SERVERS.NET.
.                       350626  IN      NS      F.ROOT-SERVERS.NET.
.                       350626  IN      NS      G.ROOT-SERVERS.NET.
.                       350626  IN      NS      H.ROOT-SERVERS.NET.
.                       350626  IN      NS      I.ROOT-SERVERS.NET.
.                       350626  IN      NS      J.ROOT-SERVERS.NET.
.                       350626  IN      NS      K.ROOT-SERVERS.NET.
.                       350626  IN      NS      L.ROOT-SERVERS.NET.
.                       350626  IN      NS      M.ROOT-SERVERS.NET.
.                       350626  IN      NS      A.ROOT-SERVERS.NET.
.                       350626  IN      NS      B.ROOT-SERVERS.NET.
.                       350626  IN      NS      C.ROOT-SERVERS.NET.
.                       350626  IN      NS      D.ROOT-SERVERS.NET.
;; Received 436 bytes from 127.0.0.1#53(127.0.0.1) in 42 ms

com.                    172800  IN      NS      F.GTLD-SERVERS.NET.
com.                    172800  IN      NS      C.GTLD-SERVERS.NET.
com.                    172800  IN      NS      E.GTLD-SERVERS.NET.
com.                    172800  IN      NS      D.GTLD-SERVERS.NET.
com.                    172800  IN      NS      B.GTLD-SERVERS.NET.
com.                    172800  IN      NS      M.GTLD-SERVERS.NET.
com.                    172800  IN      NS      L.GTLD-SERVERS.NET.
com.                    172800  IN      NS      K.GTLD-SERVERS.NET.
com.                    172800  IN      NS      G.GTLD-SERVERS.NET.
com.                    172800  IN      NS      I.GTLD-SERVERS.NET.
com.                    172800  IN      NS      J.GTLD-SERVERS.NET.
com.                    172800  IN      NS      A.GTLD-SERVERS.NET.
com.                    172800  IN      NS      H.GTLD-SERVERS.NET.
;; Received 502 bytes from 192.203.230.10#53(E.ROOT-SERVERS.NET) in 243 ms

com.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1192145590 1800 900 604800 900
;; Received 103 bytes from 192.35.51.30#53(F.GTLD-SERVERS.NET) in 227 ms


Next with the firewall up


; <<>> DiG 9.3.4 <<>> myalalla.com A +trace
;; global options:  printcmd
;; connection timed out; no servers could be reached

---

### Post by MJN on 2007-10-12
(By 'myalalla.com' I meant your domain as you'd said that's what it was! It doesn't matter though - if you can't dig google then you can't dig anything)
 
Someone with more familiarity with iptables needs to step in here as I don't use it, however - and please someone correct me if I'm wrong here - if your DNS server is sending queries out _with an ephemeral source port of >1024 (or, specifically, not 53) and a destintion port of 53_ then whilst the packet can get out (due to your anywhere anywhere OUTPUT rule) the response will not be able to get back in (due to no matching rule, other than the default reject INPUT rule).
 
Short of putting in a rule which matches replies (I'm sure that's doable) I would think a simple solution is to add a rule that allows incoming packets _with a source port of 53_ (indeed you'll need similiar rules for other servces too).
 
Can anyone else confirm this diagnosis?
 
Mathew
 
P.S. I the above is correct I'm surprised you can do anything with that firewall turned on. At least anything that has initiates client connections from that machine (e.g. web browsing). Can you confirm that this is the case? Have you implemented this (DNS server, firewall etc) all in one go? Recipe for disaster as it's often hard to tell what's at fault (like in this case you though it was a DNS/BIND issue but it's now looking like a firewall issue).

---

### Post by gishaust on 2007-10-12
Thankyou MJN

I am glad that isn't dns  and postfix. As I have been  having a problems with 
the setup of these program. But maybe that was never the issue. 

Sorry about  myalalla.com. I miss understood. If I dig with the firewall up 127.0.0.1 does the same thing. What is funny I have been running http for 6months with the same firewall settings as well as webmin and ssh and have never been an issue.

So what you are saying in response to your last post is that if I try and initiate anything out of the server(dns postfix) it is not going to work. because of the rules I have setup. Is my understanding correct?

---

### Post by MJN on 2007-10-12
I'm not entirely sure in all honesty - as I don't use iptables I'm learning on the spot as to how it works.
 
I just feel that as things currently stand any response (from the Internet) to a DNS query (from your machine) will be coming _from_ port 53 and hence is not going to match any of your incoming rules (the only domain/53-related ones are referring to _destination_ ports). No match, of course, other than the catch-all REJECT which will bin it (hence the failure).
 
Try adding two rules along the lines of:
 
ACCEPT tcp -- anywhere anywhere tcp **spt:**domain
ACCEPT udp -- anywhere anywhere udp **spt:**domain
 
(I'm sure you'll know the format/syntax better than me, but hopefully it's clear what I'm suggesting)
 
Mathew

---

### Post by gishaust on 2007-10-12
Thank you MJN

Yes it is iptables. I setup dns and postfix and sent an email to yahoo. With the firewall up and it does not work, but if I drop it works fine. great, great great. Now I have to  look at my iptables knowledge. 

Thanks again MJN for all your help. If it was not for your help I would still be blaming dns or postfix.

I do like this linux community.
Gishaust

---

### Post by gishaust on 2007-10-12
thanks again

Thanks for the suggestions on iptables. I am very new to ubuntu and firewalls I better go and read up. It is the hardest thing to do when coming from microsoft where click click click can get you some where with little knowledge or understanding. I have to stop with the howto's and read from the creators of the software. Then ask questions to get wisdom

gishaust


P.S like the reno's doing the same down here in aus but have no photos

---

### Post by MJN on 2007-10-12
Have you tried adding those two extra rules? Any different?
 
Mathew

---

### Post by siogwah on 2007-10-12
It might be helpful to add to your iptables rules a rule to allow returning packets. The output rule allows traffic but the INPUT
table is denying the return.

insert at the beginning of INPUT table
```

iptables -I INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED

```

Also I often add a LOG  rule to the end of the table so I can see whats being dropped.

Add to your INPUT table (at the end)

```

iptables -A INPUT -j LOG --log-prefix 'INPUT drop '

```

watch your logs though they may grow profusely depending on the speed of you connection etc.

---

### Post by gishaust on 2007-10-12
MJN 
Yes you were right I had no spt. I know it was a while, i went and did some study to make sure I understood what  spt was, and then decided to sleep.

Thanks for your help

siogwah

I will use that log code it will be very useful. I understand the theory with the top code but I am going to first break it down i don't understand state --state ESTABLISHED,RELATED. Understand first my new moto.

Gishaust

---

### Post by MJN on 2007-10-12
Excellent news - I think we've all learnt something!

---

### Post by milosz.galazka on 2007-10-12
Just couple of words about port 53 TCP and UDP.
You just need to pass on firewall port 53/UDP for clients.

You don't want to pass on firewall port 53/TCP to all but only to selected ip addresses.

---

### Post by gishaust on 2007-10-12
Yes your right I just trialed it without tcp. As my circumstance  only call for dns client. It works fine i can dig and it does not effect the email server

thanks

---

### Post by MJN on 2007-10-13
> **milosz.galazka said:**
> Just couple of words about port 53 TCP and UDP.
You just need to pass on firewall port 53/UDP for clients.

You don't want to pass on firewall port 53/TCP to all but only to selected ip addresses.

Ths is a bad idea.You will need port 53 open for TCP for the condition where you have an oversized (>512byte) query/response and the server does not support EDNS. In this case the truncation bit will be set and the resolver (be that at your or their end) will have no choice but to use TCP. There are other situations which require it also (signed queries/responses, UDP connectivity problems etc)

It is a popular misconception that TCP 53 is only required for zone transfers - this is incorrect.

Here's an example...

Suppose we want to query the aol.com for record type ANY. Dig will, by default, use UDP and if the response is too big to fit into 1 521 byte UDP - remember UDP is connectionless so multiple packets cannot be sent - then it will use TCP instead. Let's see this in action:

```
dig @dns-02.ns.aol.com aol.com any
;; Truncated, retrying in TCP mode.

; <<>> DiG 9.3.2 <<>> @dns-02.ns.aol.com aol.com any
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20957
;; flags: qr aa rd; QUERY: 1, ANSWER: 16, AUTHORITY: 0, ADDITIONAL: 18

;; QUESTION SECTION:
;aol.com.                       IN      ANY

;; ANSWER SECTION:
aol.com.                60      IN      A       64.12.193.85
aol.com.                60      IN      A       205.188.142.182
aol.com.                60      IN      A       207.200.74.38
aol.com.                60      IN      A       207.200.94.38
aol.com.                60      IN      A       64.12.50.151
aol.com.                300     IN      TXT     "spf2.0/pra ip4:152.163.225.0/24 ip4:205.188.139.0/24 ip4:205.188.144.0/24 ip4:205.188.156.0/23 ip4:205.188.159.0/24 ip4:64.12.136.0/23 ip4:64.12.138.0/24 ptr:mx.aol.com ?all"
aol.com.                300     IN      TXT     "v=spf1 ip4:152.163.225.0/24 ip4:205.188.139.0/24 ip4:205.188.144.0/24 ip4:205.188.156.0/23 ip4:205.188.159.0/24 ip4:64.12.136.0/23 ip4:64.12.138.0/24 ptr:mx.aol.com ?all"
aol.com.                3600    IN      MX      15 mailin-04.mx.aol.com.
aol.com.                3600    IN      MX      15 mailin-01.mx.aol.com.
aol.com.                3600    IN      MX      15 mailin-02.mx.aol.com.
aol.com.                3600    IN      MX      15 mailin-03.mx.aol.com.
aol.com.                3600    IN      NS      dns-06.ns.aol.com.
aol.com.                3600    IN      NS      dns-07.ns.aol.com.
aol.com.                3600    IN      NS      dns-01.ns.aol.com.
aol.com.                3600    IN      NS      dns-02.ns.aol.com.
aol.com.                3600    IN      SOA     dns-01.ns.aol.com. hostmaster.aol.net. 2007101201 1800 300 604800 600

;; ADDITIONAL SECTION:
mailin-01.mx.aol.com.   300     IN      A       64.12.137.184
mailin-01.mx.aol.com.   300     IN      A       64.12.137.249
mailin-01.mx.aol.com.   300     IN      A       205.188.156.248
mailin-01.mx.aol.com.   300     IN      A       205.188.159.57
mailin-02.mx.aol.com.   300     IN      A       64.12.137.168
mailin-02.mx.aol.com.   300     IN      A       64.12.138.120
mailin-02.mx.aol.com.   300     IN      A       205.188.155.89
mailin-02.mx.aol.com.   300     IN      A       64.12.137.89
mailin-03.mx.aol.com.   300     IN      A       64.12.138.153
mailin-03.mx.aol.com.   300     IN      A       205.188.109.56
mailin-03.mx.aol.com.   300     IN      A       205.188.157.217
mailin-04.mx.aol.com.   300     IN      A       205.188.159.216
mailin-04.mx.aol.com.   300     IN      A       64.12.138.57
mailin-04.mx.aol.com.   300     IN      A       64.12.138.88
dns-01.ns.aol.com.      3600    IN      A       64.12.51.132
dns-02.ns.aol.com.      3600    IN      A       205.188.157.232
dns-06.ns.aol.com.      3600    IN      A       149.174.54.153
dns-07.ns.aol.com.      3600    IN      A       64.236.1.107

;; Query time: 119 msec
;; SERVER: 205.188.157.232#53(205.188.157.232)
;; WHEN: Sat Oct 13 11:34:30 2007
;; MSG SIZE  rcvd: 1009

```Note the message size - 1009 bytes - this would not fit inside a UDP packet as we can see if we force dig to only use UDP and not retry with TCP:

```
dig @dns-02.ns.aol.com aol.com any +notcp +ignore

; <<>> DiG 9.3.2 <<>> @dns-02.ns.aol.com aol.com any +notcp +ignore
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61608
;; flags: qr aa tc rd; QUERY: 1, ANSWER: 8, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;aol.com.                       IN      ANY

;; ANSWER SECTION:
aol.com.                60      IN      A       205.188.142.182
aol.com.                60      IN      A       207.200.74.38
aol.com.                60      IN      A       207.200.94.38
aol.com.                60      IN      A       64.12.50.151
aol.com.                60      IN      A       64.12.193.85
aol.com.                300     IN      TXT     "spf2.0/pra ip4:152.163.225.0/24 ip4:205.188.139.0/24 ip4:205.188.144.0/24 ip4:205.188.156.0/23 ip4:205.188.159.0/24 ip4:64.12.136.0/23 ip4:64.12.138.0/24 ptr:mx.aol.com ?all"
aol.com.                300     IN      TXT     "v=spf1 ip4:152.163.225.0/24 ip4:205.188.139.0/24 ip4:205.188.144.0/24 ip4:205.188.156.0/23 ip4:205.188.159.0/24 ip4:64.12.136.0/23 ip4:64.12.138.0/24 ptr:mx.aol.com ?all"
aol.com.                3600    IN      MX      15 mailin-01.mx.aol.com.

;; Query time: 99 msec
;; SERVER: 205.188.157.232#53(205.188.157.232)
;; WHEN: Sat Oct 13 11:26:23 2007
;; MSG SIZE  rcvd: 502
```The response is truncated with the result that we only get half of the answer we'd got previously.

Mathew

---

### Post by gishaust on 2007-10-14
MJN I have do this right,

DNS will work with udp but if dns is asked to find a large inquiry  it will not be able to do it because it needs tcp to help with the transfere of packets.

Are the zones that you are talking about DNS zones say like the ones you create in bind?

I like the example. It was very useful. I did trial it on my home dns and yes it did the same.

Gishaust

---

### Post by milosz.galazka on 2007-10-14
Thanks for pointing me my mistake. I didn't realized that before.

---

### Post by MJN on 2007-10-15
> **gishaust said:**
> MJN I have do this right,
 
DNS will work with udp but if dns is asked to find a large inquiry it will not be able to do it because it needs tcp to help with the transfere of packets.
 
Kind of - UDP is a connectionless protocol which in effect means one packet has no connection to the next. Hence, unlike TCP, you cannot split a large amount of data in smaller chunks and send them by UDP in order to have the other side rebuild the data with the contents of each packet (re-requesting missing packets along the way) - this is where TCP comes in as you can send as much data as you like by splitting it into a stream of packets (and each packet is bigger too).
 
> Are the zones that you are talking about DNS zones say like the ones you create in bind?
 
Zones as in 'zone transfers'? These are used to transfers a copy of the entire zone (e.g. all the records - NS, A, MX etc - for your particular domain) between, usually, two name servers. Hence all you do is keep one of them (the master) up-to-date and the other (slave) periodically transfers the zone if it think it's been updated. Due to the size of these transfers (imagine a domain with thousands of hosts) TCP must be used.
 
The 'problem' here is that such information can be of use to an attacker by giving them more of an idea what your infrastructure looks like (there is a counter argument that there is little security in keeping this hidden). Hence it is quite common to wish to restrict zone transfers to particular machines and whilst blocking TCP to/from port 53 is one way of doing this it does have undesirable side-effects as discussed above. Instead, BIND has the 'allow-transfer' option to restrict such access.
 
Mathew

---

### Post by gishaust on 2007-10-15
Thankyou

  You explain things well MJN. Especially for us newbies.

Gishaust

---

