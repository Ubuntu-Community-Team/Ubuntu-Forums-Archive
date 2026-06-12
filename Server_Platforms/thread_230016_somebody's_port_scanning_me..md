---
title: "somebody's port scanning me."
date: 2006-08-05
forum: Server Platforms
---

### Post by ubiwankanubi on 2006-08-05
in a few minutes my firewall has blocked quite a lot of things, it seems that I was being port scanned.

they checked some normal and seemingly random ports from 2 to 6000.

What should i do if someone is scanning my computer?

---

### Post by philippe_carlo on 2006-08-05
Cheer for firewalls ;-)

---

### Post by _simon_ on 2006-08-05
Nothing.... it happens all the time. They won't be scanning your particular pc on purpose but rather a range of addresses.

---

### Post by ubiwankanubi on 2006-08-05
so, I don't need to unplug my computer from the internet or anything?

even with a firewall, what happens if he finds an open port? will I know about it?

---

### Post by _simon_ on 2006-08-05
Try something like this to test your posrts:

[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)

You don't need to unplug. Suprised you have only just noticed the port scans to be honest.

---

### Post by slimdog360 on 2006-08-05
how can one tell if they are being port scanned as it were?

---

### Post by _simon_ on 2006-08-05
Depends on your firewall. Some alert you constantly and some just add it to the log file.

You are probably scanned everyday but just aren't aware of it. As long as you have a decent firewall there is nothing to worry about.

---

### Post by ubiwankanubi on 2006-08-05
well, normally firestarter will log blocked connection. I get a few blocked incoming and outgoing connections every so often. But, this morning, During a 10 min or so period firestarter blocked incoming and outgoing connections about every few seconds. Also, the ports blocked were some common ports, 2, 25, 80, 67, 22, 1026, 1027, and also some other ports. The source and destination IPs of the blocked connections were mixed either unidentifiable or someone else's computer. It seemed too systematic, so I thought it was a port scan and unplugged my computer from the internet for some time.

has this happened to anyone and how did you deal with this kind of activity?

---

### Post by _simon_ on 2006-08-05
It's happened a few times in the past to me. I just ignored it satisfied that the firewall had done it's job. It's what it doesn't log you need to worry about ;)

---

### Post by slimdog360 on 2006-08-05
> **_simon_ said:**
> Depends on your firewall. Some alert you constantly and some just add it to the log file.

You are probably scanned everyday but just aren't aware of it. As long as you have a decent firewall there is nothing to worry about.


Im using guarddog and it never notifies me about anything,the way I like it, so I'll check the log.
edit: It says it logs everythin in the system log but when I check there it doesnt say anything about the ethernet connection apart from when its setting up. Is there some other logging tool for which I can do this?

---

### Post by _simon_ on 2006-08-05
> **slimdog360 said:**
> Im using guarddog and it never notifies me about anything,the way I like it, so I'll check the log.
edit: It says it logs everythin in the system log but when I check there it doesnt say anything about the ethernet connection apart from when its setting up. Is there some other logging tool for which I can do this?

Hopefully someone else can answer this. Personally i rely on my routers NAT rather than a software firewall.

---

### Post by ubiwankanubi on 2006-08-05
> _simon_  	It's happened a few times in the past to me. I just ignored it satisfied that the firewall had done it's job. It's what it doesn't log you need to worry about 
Yeah, I also see that there's some traffic that passes through even with no browsers open. I've no idea what is going in or out in this case.

how can one find out what it is? or stop some unknown packets from coming in and out?

---

### Post by ubiwankanubi on 2006-08-06
so, after doing a dns/ip search, I find that those machines are from a certain foreign company. is it possible for them to watch my network traffic and some how gain my passwords, or other info? And more importantly, how to stop or avoid them?
Should I switch ISP, move to a new location, etc.?

---

### Post by Cave Dweller on 2006-08-10
Hi.

I'm not sure if this is off topic, but I visited this website...

[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)

And it tells me that I have all sorts of ports open and unsecure.  And then, from another thread, I followed a link to this website...

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

And that one says something like; perfect and true stealth.

I was just wondering if anyone can help me out with an alternative site, because I want a third opinion.  Or an explanation, perhaps one (or both) are bogus?

I'm curious, because my new internet-modem-thingie is supposed to be some kind of firewall.  They made a special point, during the (installation / setup), to ensure all software firewalls are removed as they are no longer required and may interfere with the correct functioning of the unit.  This  made me feel quite uncomfortable, sitting there in a "naked" winxp box.  So, here I am asking questions.

Edited to add:

From another thread...

[http://scan.sygate.com/]("http://scan.sygate.com/")

Which tells me that all is well.  So that's two safe and one not-safe.

---

