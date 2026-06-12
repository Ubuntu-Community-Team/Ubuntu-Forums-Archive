---
title: "Trojan Alert"
date: 2008-09-29
forum: The Cafe
---

### Post by aaaantoine on 2008-09-29
I know this doesn't necessarily affect anyone here, but I figure someone here might be able to...

A. pass this info on to the appropriate authorities. and
B. Grab the script code to see exactly what this does.

Much appreciated.

I should clarify.  The site employs a JavaScript exploit of some sort.  Be sure you have NoScript installed (or javascript disabled in general) before visiting.

**This is a malicious site, so please tread carefully.**
**link snipped**

---

### Post by steveneddy on 2008-09-29
How did you find out about this?

---

### Post by LaRoza on 2008-09-29
I snipped the link.

A quick glance at the code shows it is trying to hide what it does.

The main thing is that is tries to use inline frames to get content onto the page, specifically, a flash object of some sort.

---

### Post by aaaantoine on 2008-09-29
> **steveneddy said:**
> How did you find out about this?

It was injected into a website I visit.  The people there are already aware of the issue.

---

### Post by aaaantoine on 2008-09-29
> **LaRoza said:**
> I snipped the link.

A quick glance at the code shows it is trying to hide what it does.

The main thing is that is tries to use inline frames to get content onto the page, specifically, a flash object of some sort.

Should I report this to Adobe then?

---

### Post by LaRoza on 2008-09-29
> **aaaantoine said:**
> Should I report this to Adobe then?

No. I can't tell what the flash object does. It *probably* makes use of the design/lack of design of IE. 

I had no effect from it and couldn't tell what the flash object was, only that it existing (referenced in the code, I opened the frames using the URI's from the scripts).

---

### Post by fatality_uk on 2008-09-29
Can't see the code but i am guessing it's the current re-working of the exploit first found in march and posted recently on /.

[http://it.slashdot.org/article.pl?sid=08/09/25/1955228&from=rss](http://it.slashdot.org/article.pl?sid=08/09/25/1955228&from=rss)

and

[http://blogs.zdnet.com/security/?p=1972](http://blogs.zdnet.com/security/?p=1972)

ClickJacking, as it's known, is a bad exploit.

[http://www.webadminblog.com/index.php/2008/09/24/new-0day-browser-exploit-clickjacking-owasp-appsec-nyc-2008/](http://www.webadminblog.com/index.php/2008/09/24/new-0day-browser-exploit-clickjacking-owasp-appsec-nyc-2008/)

From what I understand, Adobe, et al, tried to keep a lid on it. But the fact is that it's out there in the real world.

[http://ha.ckers.org/blog/20080915/clickjacking/](http://ha.ckers.org/blog/20080915/clickjacking/)

---

### Post by john_spiral on 2008-10-01
What is the level of severity for this threat?

From the name I guess you could land up messing up your wine installation with a link you never intended clicking on?

---

