---
title: "UFW blocking web requests from non port 80 sources"
date: 2011-01-11
forum: Security
---

### Post by fahdoos on 2011-01-11
I have UFW (uncomplicated firewall) setup on my web server. I'm allowing port 80, but notice tons of log messages (in /var/log/syslog) each day blocking requests for this port. The one thing strange I notice about all of these is that the source port (SPT) is a value other than 80. Checking whois against some of the IPs, it seems to be coming from my CDN provider.My question is should i be allowing all these requests, and if so how do i tell UFW to allow them?

Log Example:

 [596728.337360] [UFW BLOCK] IN=eth0 OUT= MAC=XXXX SRC=XXXX DST=XXXX LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=52520 PROTO=TCP [COLOR="Red"]SPT=51044 DPT=80[/COLOR] WINDOW=122 RES=0x00 ACK FIN URGP=0

---

### Post by bodhi.zazen on 2011-01-11
> **fahdoos said:**
> I have UFW (uncomplicated firewall) setup on my web server. I'm allowing port 80, but notice tons of log messages (in /var/log/syslog) each day blocking requests for this port. The one thing strange I notice about all of these is that the source port (SPT) is a value other than 80. Checking whois against some of the IPs, it seems to be coming from my CDN provider.My question is should i be allowing all these requests, and if so how do i tell UFW to allow them?

Log Example:

 [596728.337360] [UFW BLOCK] IN=eth0 OUT= MAC=XXXX SRC=XXXX DST=XXXX LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=52520 PROTO=TCP [COLOR="Red"]SPT=51044 DPT=80[/COLOR] WINDOW=122 RES=0x00 ACK FIN URGP=0

Well, when a client connects to you server the source port will be pseudo random, a high non-privileged port, so nothing abnormal about that.

It will connect to port 80, so nothing abnormal there.

I think you should post additional information including your rules.

Are you running a web server ?

---

### Post by fahdoos on 2011-01-11
> **bodhi.zazen said:**
> Well, when a client connects to you server the source port will be pseudo random, a high non-privileged port, so nothing abnormal about that.

It will connect to port 80, so nothing abnormal there.

I think you should post additional information including your rules.

Are you running a web server ?

Hmm, then i guess the question would be why those requests are being blocked. I am running a web server, and am able to view pages perfectly fine, and based off of analytics other people are able to view as well.

```
$ufw status verbose

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip


To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN      Anywhere
443/tcp                    ALLOW IN      Anywhere
```

any other information useful?

---

### Post by ticketswapz on 2011-01-11
Any odd messages in your error log?

---

### Post by fahdoos on 2011-01-11
> **ticketswapz said:**
> Any odd messages in your error log?

/var/log/message contains 1000's of lines with that same UFW BLOCK message just with varying ip addresses. In face i don't see any other types of errors in there.

/var/log/syslog is primarily filled with those messages and a few others, but nothing abnormal.

---

### Post by bodhi.zazen on 2011-01-11
Your rules look fine and your site is working.

My guess is that you are logging things you should not.

I typically turn logging off for ufw / iptables and use snort for NIDS. People use snort to filter through all this traffic to identify potential problems.

I seriously doubt you plan to review all those logs, so they are just taking up space.

To debug what is being dropped and why you will need to look deeper

```
sudo iptables -L -v -n
```

You can zero those numbers and watch packets getting dropped and debug why.

```
sudo iptables -Z
```

---

### Post by fahdoos on 2011-01-11
> **bodhi.zazen said:**
> Your rules look fine and your site is working.

My guess is that you are logging things you should not.

I typically turn logging off for ufw / iptables and use snort for NIDS. People use snort to filter through all this traffic to identify potential problems.

I seriously doubt you plan to review all those logs, so they are just taking up space.

To debug what is being dropped and why you will need to look deeper

```
sudo iptables -L -v -n
```

You can zero those numbers and watch packets getting dropped and debug why.

```
sudo iptables -Z
```

ok i did this and notice that 4 packets were dropped, which i think correlates to

```
    4   192 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 
```

if that's the case, is this to say it's blocking due to frequent requests?

Here's a copy of the output (but lines with 0 packets or no data removed)

```

Chain INPUT (policy DROP 4 packets, 192 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 4159  727K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 4159  727K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  223 42820 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   192 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   192 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   192 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 
Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2187 2933K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2187 2933K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  252 17314 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  252 17314 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  252 17314 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  252 17314 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    
Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  100 23350 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138  
  119 19278 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   192 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  783  480K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 2732  183K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  394 20488 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
  394 20488 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    1    28 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8  
  249 44380 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0                  
  249 44380 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  783  480K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 1152 2436K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  252 17314 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
  136  7072 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID limit: avg 3/min burst 10 
   84  4368 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   30  1752 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
  219 42628 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST     

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
  219 42628 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   59  3540 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
  193 13774 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   26  1560 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
 

```

---

### Post by bodhi.zazen on 2011-01-11
My guess is that it is due to that limit you set.

As I said, if you want to know it is most helpful to zero your count, follow your log (tail -f), and look to see where the drop comes from.

---

### Post by ticketswapz on 2011-01-11
bodhi.zazen, thanks for the tips.

---

### Post by bodhi.zazen on 2011-01-11
> **ticketswapz said:**
> bodhi.zazen, thanks for the tips.

Did you get it sorted then ?

---

### Post by fahdoos on 2011-01-12
> **bodhi.zazen said:**
> My guess is that it is due to that limit you set.

As I said, if you want to know it is most helpful to zero your count, follow your log (tail -f), and look to see where the drop comes from.

When looking further into changing the rate limit, it seems this is just a setting to limit the number of times the block would get logged, and is not actually an indication of a firewall threshold.

I turned up the firewall logs to try and sort out why only some port 80 packets are getting blocked and I think i found something. It seems that all requests with ACK FIN are blocked, and all others aren't. (see the end of first two lines below vs. the rest)

```

[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=58 ID=44808  PROTO=TCP SPT=58596 DPT=80  WINDOW=501 RES=0x00 ACK FIN URGP=0
[UFW BLOCK] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=58 ID=44808  PROTO=TCP SPT=58596 DPT=80  WINDOW=501 RES=0x00 ACK FIN URGP=0
[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=55 ID=56513  PROTO=TCP SPT=51243 DPT=80  WINDOW=491 RES=0x00 ACK     URGP=0 
[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=55 ID=56514  PROTO=TCP SPT=51243 DPT=80  WINDOW=501 RES=0x00 ACK     URGP=0 
[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=55 ID=56515  PROTO=TCP SPT=51243 DPT=80  WINDOW=501 RES=0x00 ACK     URGP=0

```

How do I allow these? I don't recall setting any to specifically block this. 

p.s. thanks for all your help so far.

---

### Post by bodhi.zazen on 2011-01-12
> **fahdoos said:**
> When looking further into changing the rate limit, it seems this is just a setting to limit the number of times the block would get logged, and is not actually an indication of a firewall threshold.

I turned up the firewall logs to try and sort out why only some port 80 packets are getting blocked and I think i found something. It seems that all requests with ACK FIN are blocked, and all others aren't. (see the end of first two lines below vs. the rest)

```

[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=58 ID=44808  PROTO=TCP SPT=58596 DPT=80  WINDOW=501 RES=0x00 ACK FIN URGP=0
[UFW BLOCK] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=58 ID=44808  PROTO=TCP SPT=58596 DPT=80  WINDOW=501 RES=0x00 ACK FIN URGP=0
[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=55 ID=56513  PROTO=TCP SPT=51243 DPT=80  WINDOW=491 RES=0x00 ACK     URGP=0 
[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=55 ID=56514  PROTO=TCP SPT=51243 DPT=80  WINDOW=501 RES=0x00 ACK     URGP=0 
[UFW AUDIT] IN=eth0 OUT= MAC=00:00 SRC=xxx.xx.xxx.xx DST=xxx.xx.xxx.xx LEN=52  TOS=0x00 PREC=0x00 TTL=55 ID=56515  PROTO=TCP SPT=51243 DPT=80  WINDOW=501 RES=0x00 ACK     URGP=0

```

How do I allow these? I don't recall setting any to specifically block this. 

p.s. thanks for all your help so far.

Well I think there are several considerations.

First, ufw. It is "easy" to learn , but hard to debug as there are a lot of rules in a lot of files.

If you really want to get into the details, I highly suggest you spend the time to learn iptables. IMO you get a buch better payoff for doing so.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

The advantage, now that you know the basic syntax of ufw, the syntax of iptables should not be that big a jump.

The second issue is logging. Most of those logs are AUDITS and honestly I would just turn off logging, especially if ufw is otherwise working.

I would say I think your limits of connections to port 80 are much too strict, Apache can handle thousands of connections, so I think little or nothing about a burst of 50 or so requests from and ip . If this resulted in a ddos, you could lower it.

Along the lines of logs, a broader question, why are you logging such detailed information ? As you can see it just fills up your logs with information that does not seem to be a problem as your site is working =)

If you want NIDS, use a tool such as snort.

---

### Post by The Cog on 2011-01-12
> It seems that all requests with ACK FIN are blocked, and all others aren't. (see the end of first two lines below vs. the rest)
A packet with a FIN flag is a request to terminate the connection. FIN = finish or final. In your example, this packet appears to be repeated, the first one being marked AUDIT and the second one marked DROP.

I wonder if this is just the tail end of a normal connection with a slightly messy shutdown. You'd need a wireshark capture in conjunction with the log to prove it, but I suspect the BLOCK action is because the firewall has already seen the connection being closed with the first FIN, so the second one doesn't belong to an open connection?

---

### Post by fahdoos on 2011-01-14
> **The Cog said:**
> A packet with a FIN flag is a request to terminate the connection. FIN = finish or final. In your example, this packet appears to be repeated, the first one being marked AUDIT and the second one marked DROP.

I wonder if this is just the tail end of a normal connection with a slightly messy shutdown. You'd need a wireshark capture in conjunction with the log to prove it, but I suspect the BLOCK action is because the firewall has already seen the connection being closed with the first FIN, so the second one doesn't belong to an open connection?

From what i can tell, ALL ack fin requests are being blocked by the firewall. I had turned up the logs to debug, so all requests show an audit log, and for any ones that are blocked an additional block log, which is why you see a duplicate for those. Really I think the issue is that the current firewall configuration is set to block ack fin requests. I'm just not sure how to change that. :confused:

---

### Post by The Cog on 2011-01-14
> **fahdoos said:**
> From what i can tell, ALL ack fin requests are being blocked by the firewall. I had turned up the logs to debug, so all requests show an audit log, and for any ones that are blocked an additional block log, which is why you see a duplicate for those. Really I think the issue is that the current firewall configuration is set to block ack fin requests. I'm just not sure how to change that. :confused:

Ah, I understand - just the one packet being audit-logged and then blocked.

I really doubt that UFW would simply block ACK FIN packets. If they belong to an existing connection then they should be allowed through. 

Since you have the audit log showing all packets, you should be able to look back in time and see if there was ever a full connection for the FIN you are seeing. If there was then the FIN should be allowed through. If not, then it should be blocked as bogus.

It would also be interesting to look through the audit log to see if you can see any valid connection where a FIN ACK actually has been allowed through. I would expect to see a FIN ACK allowed through at the end of every valid connection, except the ones that were still connected when you examined the logs.

I looked at the rules you posted, and it looks OK to me.

---

### Post by The Cog on 2011-01-14
Duplicate post deleted

---

