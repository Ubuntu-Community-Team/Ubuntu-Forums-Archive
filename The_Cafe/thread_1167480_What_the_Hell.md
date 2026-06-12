---
title: "What the Hell??"
date: 2009-05-22
forum: The Cafe
---

### Post by farlander762 on 2009-05-22
It seems to me that this should be blasphemy in the eyes of Steve Ballmer.  

[http://toolbar.netcraft.com/site_report?url=www.live.com]("http://toolbar.netcraft.com/site_report?url=www.live.com")

Is Macrosoft really running Linux?  Could even they not get their crappy OS to play right??

---

### Post by jrusso2 on 2009-05-22
IT's Akamai

---

### Post by pricetech on 2009-05-22
I'm not sure how true it is, I didn't follow up on the accuracy, but MS was aledged to have been running Linux a while back.  I heard subsequent reports that after "they got caught" they moved everything over to winders servers.

I guess you could check snopes to see if they have an entry about it.

---

### Post by MikeTheC on 2009-05-22
I can see the headlines now...

[font=arial][size=5]**MICROSOFT'S OWN IT DEPT: NO WINDOWS *HERE***[/SIZE][/FONT]

---

### Post by farlander762 on 2009-06-04
It gets better...

[http://toolbar.netcraft.com/site_report?url=http://www.bing.com]("http://toolbar.netcraft.com/site_report?url=http://www.bing.com")

What is Akamai??

---

### Post by Eisenwinter on 2009-06-04
> **farlander762 said:**
> Is Macrosoft really running Linux?  Could even they not get their crappy OS to play right??
I smell a Linux fanboy.

---

### Post by mofrikaantje on 2009-06-04
lo-ol

---

### Post by ade234uk on 2009-06-04
OK if there using Linux to run the server, what are they using to power their search, .php .pl .jsp this would be interesting to find out.

---

### Post by Tibuda on 2009-06-04
> **ade234uk said:**
> OK if there using Linux to run the server, what are they using to power their search, .php .pl .jsp this would be interesting to find out.

ASP.NET under mono.

---

### Post by Barrucadu on 2009-06-04
I seem to recall reading somewhere that their datacenter used Linux firewalls; hence the OS appears as Linux, but the servers are Windows.

Or something like that. I think.

---

### Post by benj1 on 2009-06-04
[http://en.wikipedia.org/wiki/Akamai_Technologies]("http://en.wikipedia.org/wiki/Akamai_Technologies")

explains what they do, apparently content delivery, but they use their own servers rather than (in this case) microsoft. well at least it wont crash

---

### Post by directhex on 2009-06-04
What Akami primarily do is *load balancing* - a whole bunch of caching and so on to allow really loaded sites to offload much of their bandwidth trouble.

Microsoft have been subcontracting Akami for years, as they're really very good at what they do - and whilst Akamai's service runs on Linux servers, the severs they're caching will be at Microsoft's HQ and running Microsoft's OS. You'll get the same result from a check of microsoft.com

```
jms@osc-bigmac:~$ ping www.microsoft.com
PING lb1.www.ms.akadns.net (65.55.12.249) 56(84) bytes of data.
```

---

### Post by sydbat on 2009-06-04
My question is "who cares?"

---

### Post by burvowski on 2009-06-04
> **sydbat said:**
> My question is "who cares?"

People who have posted in this thread.

---

