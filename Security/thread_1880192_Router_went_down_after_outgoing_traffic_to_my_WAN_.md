---
title: "Router went down after outgoing traffic to my WAN IP address"
date: 2011-11-13
forum: Security
---

### Post by SparTacux on 2011-11-13
I was on the forum this morning and my Router Went down and came up again 20 secs later.

LCP down
Initialise LCP
LCP is allowed to come up.

I get a few of these from time to time so don't worry about them too much - I just put it down to one of those things I put up with. This time I was reading Dangertux's write up on configuring NOSCRIPT ( nice write up by the way Danger ) and remembered all that stuff about ABE so I went digging around in my logs and found my computer had made an outgoing 'call'  on port 80 to my WAN IP address just before the router went down.

UFW allowed the traffic out. My Router actually thought the outgoing traffic was incoming traffic and blocked it. 
SOURCE 192.168.0.2, 46126 Destination x.x.93.28, 80  INBLOCK RULE MATCH 

I'm curious why my computer would send traffic to my own WAN IP address. Anyone?

---

### Post by SparTacux on 2011-11-13
Oh - come on guys - I'm not joking about this.
Did my amazing powers of observation spot a DNS Rebinding Attack or am I barking up the wrong tree ?

MODEM FIREWALL - ROUTER GOES DOWN

Nov 13 09:26:44 LCP down.
Nov 13 09:26:54 Initialize LCP.
Nov 13 09:26:54 LCP is allowed to come up.
Nov 13 09:26:55 CHAP authentication success



MODEM FIREWALL - LAN IP ADDRESS TO OUTGOING WAN IP ADDRESS
( modem doesn't know what this is and blocks it as an incoming connection  x.x.93.28 )

Nov 13 09:23:39 TCP Packet - Source:192.168.0.230,46126 Destination:x.x.93.28,80 - [INBLOCK rule match]
Nov 13 09:23:44 TCP Packet - Source:192.168.0.230,32875 Destination:91.89.94.12,80 - [HTTP rule match]
Nov 13 09:23:48 TCP Packet - Source:192.168.0.230,46126 Destination:x.x.93.28,80 - [INBLOCK rule match]
Nov 13 09:24:13 UDP Packet - Source:192.168.0.230,33308 Destination:194.72.6.57,53 - [DNS rule match]
Nov 13 09:24:13 TCP Packet - Source:192.168.0.230,43849 Destination:199.71.0.47,43 - [Whois rule match]



UFW FIREWALL AUDIT ON COMPUTER 
( Time stamp is about 30 seconds behind my Router log for some reason )
 
Nov 13 09:23:39 MyComputer kernel: [ 1468.992147] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.0.230 DST=188.121.36.239 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=64431 DF PROTO=TCP SPT=49348 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 13 09:23:39 MyComputer kernel: [ 1469.352835] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.0.230 DST=x.x.93.28 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=4352 DF PROTO=TCP SPT=46126 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 13 09:23:42 MyComputer kernel: [ 1472.352114] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.0.230 DST=x.x.93.28 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=4353 DF PROTO=TCP SPT=46126 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 13 09:23:48 MyComputer kernel: [ 1478.352110] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.0.230 DST=x.x.93.28 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=4354 DF PROTO=TCP SPT=46126 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 

It's all  rather interesting :-)
Anyone got any ideas as to why my computer made links to my WAN IP ( x.x.93.28 )

---

### Post by SparTacux on 2011-11-13
It still doing it with WAN IP £ LOCAL set in NOSCRIPT ( ABE Menu ) LOL 
So much for that Theory ;-)

mmmmmm

ok guys - I'm prepared to negotiate your surrender details
Lets call it a Draw and call it quits shall we :-)

---

### Post by OpSecShellshock on 2011-11-13
So you have confirmed that the IP address you are concerned about is, in fact, your public IP address? Also, have you identified the process that is making the request? Do you have a web server on your network somewhere? Log files alone may not provide sufficient information.

---

### Post by SparTacux on 2011-11-14
> **OpSecShellshock said:**
> So you have confirmed that the IP address you are concerned about is, in fact, your public IP address? Also, have you identified the process that is making the request? Do you have a web server on your network somewhere? Log files alone may not provide sufficient information.

Duh - FALSE ALARM - It was actually  NOSCRIPT that was actually doing it. It seems that feature to check for DNS Rebinding Attacks needs to get your WAN IP Address for it to work.  I suspect the Router going down was just a glitch in my Router and had nothing to do with the probe to get the IP address. Amazing.

Well at least I know what an attack targeting your Router WAN IP Address looks like should I ever be on the end of one. It lights my Router up like a Beacon. All I need to do is to check the modem logs for the Source IP coming from my private network with a BLOCK message on port 80. It will be a nice exercise to go through my logs using grep ( or something similar ) to look for one.  

That's the Theory ;-)

---

