---
title: "port 113 no longer stealthed, shows as &quot;closed&quot; with cable internet"
date: 2009-03-26
forum: Security
---

### Post by zaphodbblx on 2009-03-26
Just got hooked up with time warner. I also use their VOIP service..for some reason when I hooked up to their modem it unstealthed port 113 (although its marked as closed) any one know why? is it because of the voip? or is it something to do with cable internet service. any idea how to re-stealth it?

---

### Post by cdenley on 2009-03-26
[http://forums.wi-fiplanet.com/showthread.php?t=2676](http://forums.wi-fiplanet.com/showthread.php?t=2676)

Why do you want it "stealthed"? Rejecting an incoming connection instead of ignoring it doesn't really create a security risk. If it is your ISP's modem (or your ISP) that wants to reject connections on that port, you probably can't do anything about it. If it is your router, then there is probably an option in it's configuration.

---

### Post by zaphodbblx on 2009-03-26
> **cdenley said:**
> [http://forums.wi-fiplanet.com/showthread.php?t=2676](http://forums.wi-fiplanet.com/showthread.php?t=2676)

Why do you want it "stealthed"? 


No reason really! just it used to be stealthed when I had dsl but now it isnt with cable....just wondering why is all:popcorn:
I pretty much decided to leave it be

---

### Post by bodhi.zazen on 2009-03-26
"Stealth" sounds cool , but it is probably no more secure then "Closed", although the topic is at times hotly debated.

I suggest you take a look at "proper syntax" for the linux firewall, iptables and learn the difference between DROP and REJECT

DROP = "stealth"
REJECT = "closed"

Once you understand the terminology you should be able to decide for yourself.

---

### Post by zaphodbblx on 2009-03-26
> **bodhi.zazen said:**
> "Stealth" sounds cool , but it is probably no more secure then "Closed", although the topic is at times hotly debated.

I suggest you take a look at "proper syntax" for the linux firewall, iptables and learn the difference between DROP and REJECT

DROP = "stealth"
REJECT = "closed"

Once you understand the terminology you should be able to decide for yourself.
seems one is just as good as the other heh?
thanks for all the help though...seems like I have some reading to do

---

