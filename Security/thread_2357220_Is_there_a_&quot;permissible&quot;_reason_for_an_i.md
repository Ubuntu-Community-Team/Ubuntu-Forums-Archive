---
title: "Is there a &quot;permissible&quot; reason for an ip to make an &quot;inbound request&quot;? Client Deksto"
date: 2017-03-31
forum: Security
---

### Post by whereismymindat2 on 2017-03-31
Is there *EVER* a "permissible" reason for an IP to make an "inbound request"? Client Desktop. 
Of course I know this excludes any programs that (obviously) "Need" inbound access (Desktop Sharing). Team Viewer, et.al. 


However, Peerguardian showing that Comcast just went *CRAZY* when Comcast IP ranges were trying all types of inbound connections on 80 and 443
(should be noted was not "Surfing"). Was reading a page on something..heard drive thrashing....opened up Peerguardian to my shock. 


 I use a VPN (PIA) thus why not making my 10.1.x address (it's always different connecting). 

Comcast makes me "suspicious."
(A VPN of course bypasses that). 


Then Twitter makes *NO SENSE* ---because I don't have a "Client" installed on my machine. Nor do I have it open in a browser (don't even really use Twitter). 


As well as Apple (I don't even own an IOS). I have Android. |}
I did a whois..that's a Cuptertino address (someone said the server(s) are in the U.K. though). 




Any reason this occurring?[ATTACH=CONFIG]274372[/ATTACH][ATTACH=CONFIG]274373[/ATTACH][ATTACH=CONFIG]274374[/ATTACH]

---

### Post by wildmanne39 on 2017-03-31
*Thread moved to **Security**.*

---

### Post by Habitual on 2017-03-31
Just a "guess"... Your ISP is scanning for "services" it considers out-of-contract?

---

### Post by bashiergui on 2017-04-01
Best way to find out is to capture packets. You can use wireshark or tcpdump. Without reviewing you're left guessing.

That said, I've seen lots of Twitter connections like that when I browse to a web page that has a Twitter icon. The other stuff could be ads getting served on the page you're on. But again, only way to know for sure is to review the packets.

---

### Post by SeijiSensei on 2017-04-01
> **Habitual said:**
> Just a "guess"... Your ISP is scanning for "services" it considers out-of-contract?

Pretty much every Comcast subscriber has an ISP-provided NAT router, so I'm not sure how machines on the Internet can address the computer behind the router like the OP reports.  Perhaps the router itself is doing some scanning as you suggest.

---

### Post by The Cog on 2017-04-01
Looking at those screenshots, in every case the **source** port of the blocked incoming packet is either 80 or 443 (http or https web server) and the destination port is 54??? (high numbers are normally used when initiating outgoing calls). These appear to be **responses** from web services, addressed to you as though you tried to contact them. So either you have been talking to these servers recently, or something else has been, using your IP address. Without more detailed packet traces, I can't guess what is really happening. Maybe your ISP have allocated your address to two users and someone else somewhere is having difficulty talking to these servers because the responses are going to you.

---

