---
title: "Am I being brute forced!?"
date: 2009-02-03
forum: Security
---

### Post by spinanicky on 2009-02-03
Hi guys,

I have been monitoring netstat -tap and iftop to see whats going on on my server. Something that is worrying me is the apparent random connections I am getting?!

Please see pictures of netstat and iftop for details.

Thanks for the help.

ps: If you need caps of anything else let me know

---

### Post by HermanAB on 2009-02-03
Iptables nowadays has a very nice rate limit module which can prevent all kinds of abuse:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT


Cheers,

Herman

---

### Post by spinanicky on 2009-02-04
as far as I can understand that code that is allowing 30 connections per minute... that's one every two seconds. Would you not say that is a bit high?!

Also can you confirm that they are just random connections to random ports or are they actually due to a port that is being listened to?!

Another quick point, does iftop show everything that passes on the Ethernet? ie does it show connections that are refused as well or only connections that are "connecting" or getting a response?

---

### Post by brian_p on 2009-02-04
> **spinanicky said:**
> as far as I can understand that code that is allowing 30 connections per minute... that's one every two seconds. Would you not say that is a bit high?!

Alter it to suit.

> Also can you confirm that they are just random connections to random ports or are they actually due to a port that is being listened to?!

Connections can only be made to a port which has a listening process on it. As for this randomness - what is there in your screenshots which show this?

> Another quick point, does iftop show everything that passes on the Ethernet? ie does it show connections that are refused as well or only connections that are "connecting" or getting a response?

iftop displays bandwidth usage information on an network interface so I expect so.

---

### Post by spinanicky on 2009-02-04
The last 7 or so connections should not be there as far as I am concerned or do you guys see a reason for them to be there based on what is being listened to?

---

