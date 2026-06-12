---
title: "Ipv6"
date: 2012-10-09
forum: Security
---

### Post by jmore9 on 2012-10-09
Hello

I saw this on the firewall log and was wondering if it could be comcast starting up IPV6 in my area ?  It caught my attention because of the 
192.88.99.1 source.

Anyone have any ideas ? Check into it or ignore it ?

---

### Post by Ms. Daisy on 2012-10-09
What you posted is an IPv4 address...  I would need to see more of the log to help you. The ports & protocols are important. If it's a snippet of a ufw log, then give the whole line, just anonymise your IP.

---

### Post by lemming465 on 2012-10-13
192.88.99.1 is the 6to4 anycast relay address (IPv4 side), which is a fairly bad kind of tunneled IPv6; measurements from Geoff Huston at APNIC show about 30% connection failure rate for TCP over 6to4.  Comcast already has over 50% of its subscriber base wired for native IPv6, and should complete its v6 consumer rollout sometime in 2013, so you are quite likely to see v6 fairly soon if they are your ISP.  

You will probably have to replace (or at the very least upgrade firmware) both your broadband modem and your wifi router (if that's a separate device) to get end-to-end v6.  For cable modems the key blurb point is "DOCSIS 3".  Bonus points for certified IPv6 compliance with DoD or NIST profiles, particularly if done by one of the better testing labs such as the University of New Hampshire.

The #1 sign of native IPv6 is seeing IPv6 ICMP router advertisement messages from your uplink.  You can probe for them with *rdisc6*.  *ip address show* will exhibit inet6 family addresses starting with "2" (global unicast scope), not just the automatic ones starting with "fe80" (link-local LAN scope).  Your router address will always be link-local.

If you want to test v6 before your ISP-modem-wifi network chain supports it, I sugest using a free 6in4 tunnel from one of the brokers, such as sixxs, gogo6, or Hurricane Electric ("tunnelbroker.net").  I don't recommend the automatic 6to4 or Teredo (package: "miredo") tunnels.

Once you have native v6, expect that some but not all of your destinations will use it.  Google, Youtube, Netflix, Xbox and a few others offer content over v6 and v4 already; more will come.  I'm not aware of any v6-only content yet, so the urgency of consumers deploying v6 is still low, but the tipping point could be sooner than you think, e.g. Christmas 2014 in some talks I've done.  However, if you have any interest in IP networking, IPv6 is definitely the future of the internet, and the sooner we all get familiar with it, the better.  Do the math: over 6 billion live cellphones, with an increasing percentage of smartphones and data plans, versus only about 3 billion usable IPv4 addresses.  Never mind all of computer users :-)  In the US, the LTE4 phone networks are *already* IPv6-only; getting to the legacy v4 internet from them requires going through a NAT64 gateway at the carrier.  AT&T and Cisco are projecting that global backbone routing for IPv4 will be turned off around 2020, though I predict the last IPv4 device won't be decommissioned until 2036.

---

### Post by Ms. Daisy on 2012-10-13
> **lemming465 said:**
> 192.88.99.1 is the 6to4 anycast relay address (IPv4 side), which is a fairly bad kind of tunneled IPv6; measurements from Geoff Huston at APNIC show about 30% connection failure rate for TCP over 6to4.... fascinating. Obviously I wasn't aware of that. Thanks for the info.

---

