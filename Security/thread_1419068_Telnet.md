---
title: "Telnet ?"
date: 2010-03-01
forum: Security
---

### Post by MooPi on 2010-03-01
Can anyone tell me why my Internet provider would attempt to TELNET onto my home network? Lets just say it concerns me. Is there a legitimate reason ?

---

### Post by MooPi on 2010-03-01
I'm guessing no from the zero responses. I think I'll give them a call this afternoon to discuss the situation.

---

### Post by FuturePilot on 2010-03-01
Perhaps some more info might help. Do you have some type of logs of this occurring? How do you know it's from your ISP? I would hope you're not running a telnet server?

---

### Post by MooPi on 2010-03-01
My firewall logs all blocked connections. I simply traced it back and it shows my IP. Simple home setup nothing more, in fact I don't even have a home server set up.

---

### Post by FuturePilot on 2010-03-01
I'm not sure how you were able to pinpoint that it was someone **at** your ISP. I think it's probably more likely that it's some [s]hacker[/s] cracker **on** the same ISP as you, in which case it's just another normal day on the Internet. ;)

---

### Post by MooPi on 2010-03-01
Log file:

> 67.78.0.146 (rrcs-67-78-0-146.se.biz.rr.com)
BW whois 5.0 by Bill Weinman ([http://whois.bw.org/](http://whois.bw.org/))
Copyright 1999-2006 William E. Weinman
Request: 67.78.0.146
connected to whois.arin.net [199.212.0.43:43] ... 

OrgName:    Road Runner HoldCo LLC 
OrgID:      RCSW
Address:    13241 Woodland Park Road
City:       Herndon
StateProv:  VA
PostalCode: 20171
Country:    US

ReferralServer: rwhois://ipmt.rr.com:4321

NetRange:   67.78.0.0 - 67.79.255.255 
CIDR:       67.78.0.0/15 
NetName:    RR-COMM
NetHandle:  NET-67-78-0-0-1
Parent:     NET-67-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.BIZ.RR.COM
NameServer: NS2.BIZ.RR.COM
NameServer: DNS4.RR.COM
Comment:    
RegDate:    2004-01-29
Updated:    2005-04-01

OrgAbuseHandle: ABUSE10-ARIN
OrgAbuseName:   Abuse 
OrgAbusePhone:  +1-703-345-3416
OrgAbuseEmail:  [email]abuse@rr.com[/email]

OrgTechHandle: IPTEC-ARIN
OrgTechName:   IP Tech 
OrgTechPhone:  +1-703-345-3416
OrgTechEmail:  [email]abuse@rr.com[/email]

---

### Post by FuturePilot on 2010-03-01
I think you're misinterpreting the whois info. whois only tells you who owns the IP address. In this case Road Runner/Time Warner. It does not tell you who is behind that specific IP address. And really there is no way to find that out. Run whois on your own IP address. You will see something very similar.

---

### Post by pricetech on 2010-03-01
> **FuturePilot said:**
> I'm not sure how you were able to pinpoint that it was someone **at** your ISP. I think it's probably more likely that it's some [s]hacker[/s] cracker **on** the same ISP as you, in which case it's just another normal day on the Internet. ;)

I concur.  The first few times you look at router logs it kind of freaks you out because you think it's YOU they are targeting.  After a while though you realize that sort of activity goes on all the time towards pretty much everybody.

To paraphrase FuturePilot; it's just another miserable day here in paradise.

---

### Post by TurnOfTide on 2010-03-01
How would you know that they tried to use telnet specifically? Telnet doesn't leave any sort of trace/user-agent. it just opens a raw socket connection and can easily mimic any client, you would never know it was telnet unless you had some way of logging how fast the input was generated (ie: typing HTTP request is way slower than firefox).

---

### Post by skillllllz on 2010-03-01
> **TurnOfTide said:**
> How would you know that they tried to use telnet specifically? Telnet doesn't leave any sort of trace/user-agent. it just opens a raw socket connection and can easily mimic any client, you would never know it was telnet unless you had some way of logging how fast the input was generated (ie: typing HTTP request is way slower than firefox).

I think maybe they tried connecting to his machine's port 23.

@MooPi are you running telnetd on your machine, but using the FW to manage connections to it?

---

