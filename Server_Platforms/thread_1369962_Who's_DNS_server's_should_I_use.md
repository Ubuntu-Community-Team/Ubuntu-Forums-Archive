---
title: "Who's DNS server's should I use?"
date: 2010-01-01
forum: Server Platforms
---

### Post by volkswagner on 2010-01-01
I have a couple domains with GoDaddy.com.  I have nearly completed my migration from home server to VPS as [Fivebean]("http://fivebean.com/index.php").  

I am/was using DynDns to forward.

Should I use GoDaddy's DNS servers and control panel to forward to my static IP at Fivebean?

Should I use the DNS servers at Fivebean and their control panel to manage subdomains and such?

To be honest I have always felt GoDaddy's site to be sluggish and unresponsive at times, but that would be a small price to pay if I get better/more reliable service using their servers.

Are there any other things to consider, pros/cons with each method?

---

### Post by ratcheer on 2010-01-01
My preference is OpenDNS.

Tim

---

### Post by Grim76 on 2010-01-01
Use which ever one will give you the amount of control/ease that you want to have.  It all depends on what you want.

---

### Post by volkswagner on 2010-01-02
Thanks for the suggestions.

I think I have made my decision.

GoDaddy's site sucks.  I am forever having to restart FireFox.  I also tried Google Chrome.  The site is forever trying to load, and mostly just hangs.  Yesterday I purchased two more domains.  At final payment processing just hung with a white screen indefinitely.  I let it run and opened a new browser logged in and saw my two new domains.

Does anyone else see this annoying nonsense with FireFox on Linux using GoDaddy's site?  

I still have issues using Google Chrome, but didn't expect much since it is truly Beta.

That alone points me to go with my VPS's DNS servers and control panel.

Hmn, I may have to start a new thread: POLE-"what browser do you use with GoDaddy.com?"

---

### Post by HighCommander540 on 2010-01-02
> **volkswagner said:**
> Thanks for the suggestions.

I think I have made my decision.

GoDaddy's site sucks.  I am forever having to restart FireFox.  I also tried Google Chrome.  The site is forever trying to load, and mostly just hangs.  Yesterday I purchased two more domains.  At final payment processing just hung with a white screen indefinitely.  I let it run and opened a new browser logged in and saw my two new domains.

Does anyone else see this annoying nonsense with FireFox on Linux using GoDaddy's site?  

I still have issues using Google Chrome, but didn't expect much since it is truly Beta.

That alone points me to go with my VPS's DNS servers and control panel.

Hmn, I may have to start a new thread: POLE-"what browser do you use with GoDaddy.com?"

No, its just goDaddy the site sucks...

---

### Post by BkkBonanza on 2010-01-02
I don't like GoDaddy at all. I use Name.com - very functional control panel and site seems always responsive. Also good prices on names. I tested their dns with some online tools and they were amongst the fastest I could find. Also they have Google apps integrated so you can enable them in the control panel. I've found that handy for quickly setting up email.

You could try zoneedit.com. sitelutions.com has free dns that I used for a couple years (before name.com) even though I registered elsewhere. They have a messy control panel but the dns speed is good.

There is a lot of choices out there. I've used about 4 or 5 over the years and the best yet for me has been name.com. When you buy names always google for coupons as you can usually save a dollar or two.

BTW I don't think OpenDNS offers authoritative DNS, just caching. Or am I wrong there?

---

### Post by ratcheer on 2010-01-02
OpenDNS is not the fastest, but it provides many useful features. On the other hand, many people do not like OpenDNS because of the features. As always, it is a matter of personal preference.

About a month ago, I used Steve Gibson's DNS Benchmark program to identify the fastest DNS servers for my particular connection. I used them for about a week and they were, indeed, noticeably faster. However, I missed the features of OpenDNS and went back to it. Faster is not always everything.

OpenDNS is one of the most immune services to the "DNS poisoning" attacks that were very serious a year or so ago. Some of the top DNS's are still susceptible.

Tim

---

### Post by iponeverything on 2010-01-02
Google just started offering free dns services..

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

8.8.8.8
8.8.4.4

they vow no stupid redirection or other quackery.

---

### Post by BkkBonanza on 2010-01-02
OpenDNS and Google both offer DNS caching not authoritative DNS. The OP is asking about authoritative DNS not caching, so your suggestion to use them is not appropriate to this question.

If you don't know the difference then please read up before suggesting information that is incorrect.

---

### Post by iponeverything on 2010-01-02
> **BkkBonaza said:**
> OpenDNS and Google both offer DNS caching not authoritative DNS. The OP is asking about authoritative DNS not caching, so your suggestion to use them is not appropriate to this question.

If you don't know the difference then please read up before suggesting information that is incorrect.

Oh. Please forgive me. You are correct.  

You only posted to chastise those who you assume didn't understand the original query, and not to offer answers yourself to OP with regard to a place host his zone files? How very kind.

Edit: I see you did in post 6. Again, my apologies - perhaps I should read though a thread before adding to it..

---

### Post by ratcheer on 2010-01-02
> **BkkBonaza said:**
> OpenDNS and Google both offer DNS caching not authoritative DNS. The OP is asking about authoritative DNS not caching, so your suggestion to use them is not appropriate to this question.

If you don't know the difference then please read up before suggesting information that is incorrect.

OK. Then, please tell us where we could do suitable research to learn this information. Thank you.

---

### Post by BkkBonanza on 2010-01-02
There is a reasonable write up on Wikipedia,
[http://en.wikipedia.org/wiki/Name_server](http://en.wikipedia.org/wiki/Name_server)

Authoritative DNS is the server setup for or by administrators (owners) of a domain name. Like a "master" name server that tells other (recursive or caching) name servers what IP to use for a name. 

I use Google and OpenDNS as well and they are both fine. Google and OpenDNS both have to get the IP from somewhere first before they can cache it for end users. They make a series of requests that end up at the authoritative name server configured by the site owner. This name server contains the original record defined by the site admin. That's what the question in this post was about.

Sorry, didn't mean to be offensive. Just, people should read and understand the question before answering.

---

### Post by R.Bucky on 2010-01-02
I used namebench to determine that OpenDNS was fastest where I am located (WA state). However, I have included Google DNS at work because the Comcast DNS kept pushing connection errors. Since adding Google, there have not been any problems. Benchmarks indicate that Google DNS are fairly slow ([http://buckycomputing.net/blog/check-the-fastest-dns-servers-on-your-computer-using-namebench/]("http://buckycomputing.net/blog/check-the-fastest-dns-servers-on-your-computer-using-namebench/")). Depends on your location.

---

### Post by Vegan on 2010-01-02
I installed BIND9 and fend for myself.

---

