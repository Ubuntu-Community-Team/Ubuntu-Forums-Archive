---
title: "General security question"
date: 2014-07-04
forum: Security
---

### Post by Barney-R on 2014-07-04
This may seem trivial, but could somebody please tell me exactly what information my computer is giving out every time I visit a website?

I'm aware that sites can "see" my IP address, operating system and browser, but recently it's becoming obvious that they also "know" exactly where I am, and that's quite worrying.

It's not a cookie problem. I only accept cookies from sites I trust, and I use Better Privacy to deal with Adobe's "LSO" abomination. I also use AdBlock Plus and Ghostery.

I'm in England, and occasionally I've seen advertising targetting my location. I first noticed this on a site based in Canada and hosted in the US.

 Yesterday I visited a site I'd never been to before, hosted in Germany I believe, only to be confronted with an entire page of clubs and activities in my home town.

This just seems wrong to me, and I'm wondering what other information my computer is giving out without my knowledge or consent.

I'm not so paranoid as to think I need to "hide" behind something like TOR, but I'd appreciate a complete list of **all** the information websites are able to collect about me.

---

### Post by Bucky Ball on 2014-07-04
*Thread moved to **Security Discussions**.*

---

### Post by kc1di on 2014-07-04
Geo location of your Server's IP address is possible and if it's close by that may explain why they get so close with their Advertizing. 
Also google if you using them for search, indexes you searches and presents advertizing accordingly. 
you can defeat the google thing by using a different search engine like Duck Duck go . 
In fact[ here's a page t]("http://www.iplocation.net")hat will locate you according to your servers IP address.
so if your server passes your machine IP on it can be located. 
Cheers

---

### Post by buzzingrobot on 2014-07-04
Organizations like internet service providers acquire ranges of IP addresses for their use.  Those assignments are publicly available. ISP's then assign individual IP's to their customers. (Typically, this is done automatically via DHCP running on your machine.) Service areas for ISP's are also known. So, that's one way to get a fix on where a machine using a given IP address is located.  E.g., I'm in the U.S., so a range of BBC content -- iPlayer, etc. -- is not available. But, if I use a VPN and an IP address the BBC identifies as UK-based, then it is.

A great deal of hardware also contains GPS chips which will happily announce your location unless you turn it off.

---

### Post by open2reason on 2014-07-04
Barney-R
in addition to the addons you have listed may I also  suggest using Noscript coupled with RequestPolicy?

These two when taken together give one an idea of what is asking to run (Noscript) in your browser and what requests are being made to other sites (RrequestyPolicy). With this new information you could attempt to block all that you do not require - something along the lines of white listing applications and requests you feel are safe.
You may find it instructive to visit TheGuardian.com site with both addons enabled and see just what is requesting permission to run.

---

### Post by HermanAB on 2014-07-04
The only way you will ever know what is going over the wire is with netstat and tcpdump.

---

### Post by Barney-R on 2014-07-04
Thank you all for your prompt responses. At least now I've got a better understanding of what's going on.

I'd rather not use NoScript, having found it to be more of an annoyance than it's worth, but I do have Java disabled.

Is there any other information my computer is broadcasting though? These are the ones I know about.

IP address (and now I know how sites can locate me)
Operating System (Ubuntu 12.04)
Browser (FireFox)

I note the comment about GPS, but it may not apply as I'm using a desktop machine and wired connections (internet, keyboard, mouse). Nothing "wireless" here.

Is there anything else?

---

### Post by Bucky Ball on 2014-07-04
Minor, but I use [Duckduckgo]("https://duckduckgo.com/") as a search engine. You can create a profile and browse with it.

---

### Post by open2reason on 2014-07-04
Barney-R,
The EFF  Panopticlick project [https://panopticlick.eff.org/](https://panopticlick.eff.org/) illustrates the information that may leak from your browser to form a finger print. You may wish to take the test and ponder the results.

---

### Post by Barney-R on 2014-07-04
Thanks for that, open2reason (and everyone else). I took the test, and there's a lot more there than I'd ever have suspected. Most of it's harmless, but I'd never voluntarily publish all that. Perhaps we need someone to come up with a **really** secure browser, one that will only give out the bare minimum necessary to do it's job, but I suspect we'll have a long wait.

I use Start Page for searches, though DuckDuckGo is available in the search box. Perhaps it's time I tried it.

Btw, netstat and tcpdump were a bit beyond my level of knowledge.

Thanks again everyone. I'll mark this thread as solved.

---

### Post by buzzingrobot on 2014-07-04
Much of what happens is based on how the net is structured and works.  A server needs to know your IP address, otherwise it can't return packets to you. If it knows which browser it is responding to, and which plugins are enabled on that browser, it can modify the content it sends to that browser. That can mean ads, or it can mean sending you HTML5 when you don't have Flash enabled so you still see the video clip instead of a big black rectangle.

Without tailoring content like that, web sites would either aim for the lowest common denominator or tailor only for the larget audience -- Windows and Apple -- leaving Linux behind.

Cookies are a mixed bag.  Often very convenient, often not so much.

The primary security threat today, I imagine, is not from info leaking out of browsers, or even virus attacks on Windows, but people happily entering data into bogus sites linked in legit-looking mail that seems to come from people you know.

---

### Post by bashiergui on 2014-07-05
> Perhaps we need someone to come up with a really secure browser, one that will only give out the bare minimum necessary to do it's job, but I suspect we'll have a long wait.Aviator is a browser designed for security and privacy. It's only available on Mac OSX and Windows (no mobile platforms). But I understand there are plans for expansion. 
[https://www.whitehatsec.com/aviator/](https://www.whitehatsec.com/aviator/)

---

### Post by Bucky Ball on 2014-07-05
As mentioned, DuckDuckGo does what it can, not that that's a heap, but at least an effort.

---

