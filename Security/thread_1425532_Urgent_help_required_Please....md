---
title: "Urgent help required Please..."
date: 2010-03-09
forum: Security
---

### Post by ReggieRareBreed on 2010-03-09
This is my 1st post and being a newbie with Ubuntu, I could really do with a little urgent help.
My PC has been trying to connect 'out' to an ip address at Manchester Uni.
It then goes 'out' to Didcot in Oxford.
Then 'out' again to Manchester Uni but on a different ip address?
I have got firestarter running, and this has been logged.
The main issues I have is:
 Why should my PC try to contact Man Uni in the 1st place.
What the hell is going on?
I have been 'hit' by so many different ip addresses in the last 2 weeks, my bandwidth is slowly disappearing....

Any help very much appreciated as I will be sitting here all day to try and get this PC safe for my use.

Cheers
ReggieRareBreed

---

### Post by Grenage on 2010-03-09
NTP?  Is this a fresh install, what are the IPs?

It's rather common for green users to see all these connections and assume bad mojo is occurring, but when you're on the internet there are many things that might be going back and forth.  Panic not.

---

### Post by ReggieRareBreed on 2010-03-09
[QUOTE=Grenage;8938966]NTP?  Is this a fresh install, what are the IPs?

Cheers Greenage for the quick response.......
this is a new ubuntu install, but I do have a winxp install on same hard drive?

13:03:16 direction Unknown eth0 out port 631 source 92.237.49.152 destination ip 92.237.51.255 protocol UDP service lpp

13:03:27 dir unknown  eth0 out  port 123 source ip 92.237.49.152  destination ip 130.88.200.4 protocol UDP service NTP

13:03:29 direction unknown  eth0 out port 123 source ip 92.237.49.152  dest ip 130.88.202.49  protocol UDP service NTP

13:03:34  direction unknown  eth0 out port 123 source ip 92.237.49.152 dest ip 193.62.22.98  protocol UDP service NTP

This has been going on for weeks, I have had the logs show that these incidents are happening between 1 second to every 2 to 3 seconds on the trot...
My bandwidth is slowing down...

---

### Post by cdenley on 2010-03-09
The first one appears to be something for CUPS. Is that another IP you own? If not, it appears to share the same ISP. The other 3 are going to public NTP servers, which shouldn't generate much traffic at all. If you're filtering the NTP queries, then it is probably trying another server after the query fails.

---

### Post by Grenage on 2010-03-09
As I suspected, NTP; many Universities host Time Servers.  It doesn't look like you have anything to worry about.

---

### Post by ReggieRareBreed on 2010-03-09
[QUOTE=cdenley;8939347]The first one appears to be something for CUPS. Is that another IP you own? If not, it appears to share the same ISP. 

Many thanks...
The other ip 92.237.51.255 seems to be me, but why is it trying to go out?
When I tried to ascertain who these ip addresses were, I tried to do a scan on my pc using UMit network scanner, and within 10 seconds of the scan completing, I was hit for about 30 seconds from ip 10.7.72.1????
I have tried to find on whois, but comes up with 'nothing'???
 Since putting this post up, I have had 54 serious inbounds, any answers please.

How do I stop the NTP going out?

Cheers

---

### Post by Grenage on 2010-03-09
You can disable NTP if you don't want your clock to be accurate, or modify its settings to change frequency.

I _really_ wouldn't worry about 54 in-bound connection attempts, your average PC is likely to get thousands of attempts.  That's why you have a firewall.

---

### Post by ReggieRareBreed on 2010-03-09
> **Grenage said:**
> You can disable NTP if you don't want your clock to be accurate, or modify its settings to change frequency.

I _really_ wouldn't worry about 54 in-bound connection attempts, your average PC is likely to get thousands of attempts.  That's why you have a firewall.

OK, many thanks again..... will have to do a bit of studying I think....
By the way, I just love the Ubuntu approach, windaz can just go away now.....

---

