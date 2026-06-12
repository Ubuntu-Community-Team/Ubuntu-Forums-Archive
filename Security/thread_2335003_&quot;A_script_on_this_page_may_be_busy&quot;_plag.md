---
title: "&quot;A script on this page may be busy&quot; plague"
date: 2016-08-24
forum: Security
---

### Post by xenon3 on 2016-08-24
This I have a couple of times in the week, firefox session is maybe 2 to 4 hours old, then screen gets grey for a couple of minutes, system becomes slow, than slower and finally non responsive. I get messages like:

===
A script on this page may be busy, or it may have stopped responding. You can stop the script now, open the script in the debugger, or let the script continue.

 Script: [http://ams1-ib.adnxs.com/ab?e=&#8230;m%2Fraisins-can-use-can-eat%2F:0](http://ams1-ib.adnxs.com/ab?e=&#8230;m%2Fraisins-can-use-can-eat%2F:0)
===

I immediately shutdown browser and start it up again, but message comes back (with other URL)

For instance: ams1-ib.adnxs.com is not a website I had open, the Query String is page from a website I had open (about how healthy raisins are)

To get rid of it for a couple of days, I reboot and hope for the best, this shuts down the script temporary, I do not leave computer on for days without end by the way, at night I suspend, in my windows days, regularly unprovoked system "wake up on LAN" happened

QUESTIONS:


[LIST=1]
[*]Is someone messing with my system? 
[*]What can I do about the script? 
[*]Can an UBUNTU system also be awaken on LAN? 
[/LIST]

---

### Post by &amp;KyT$0P# on 2016-08-24
1) No you are probably not being hacked, that site has been repeatedly troublesome for causing such warnings.

2) Install [NoScript]("https://noscript.net/") (or some other means to block the script)

---

### Post by coldraven on 2016-08-24
+1 for NoScript

---

### Post by HermanAB on 2016-08-27
I find Ghostery to be quite a bit more convenient than Noscript:
[https://www.ghostery.com/our-solutions/ghostery-browser-extension/](https://www.ghostery.com/our-solutions/ghostery-browser-extension/)

---

### Post by coldraven on 2016-08-27
> **HermanAB said:**
> I find Ghostery to be quite a bit more convenient than Noscript:
[https://www.ghostery.com/our-solutions/ghostery-browser-extension/](https://www.ghostery.com/our-solutions/ghostery-browser-extension/)

I run NoScript **and** Ghostery!

---

### Post by cogset on 2016-08-27
> **xenon3 said:**
> This I have a couple of times in the week, firefox session is maybe 2 to 4 hours old, then screen gets grey for a couple of minutes, system becomes slow, than slower and finally non responsive. I get messages like:

===
A script on this page may be busy, or it may have stopped responding. You can stop the script now, open the script in the debugger, or let the script continue.

 Script: [http://ams1-ib.adnxs.com/ab?e=…m%2Fraisins-can-use-can-eat%2F:0](http://ams1-ib.adnxs.com/ab?e=…m%2Fraisins-can-use-can-eat%2F:0)
===

I immediately shutdown browser and start it up again, but message comes back (with other URL)

For instance: ams1-ib.adnxs.com is not a website I had open, the Query String is page from a website I had open 

That's because it's not an user-facing (regular) website, it's a third-party service that you don't need at all: NoScript, as suggested, will take care of this.

I'd also suggest to insert this site and all its likes in a hostfile (/etc/hosts) , just in case: that will add another barrier.

Finally, if you aren't using one already, I'd also recommend an adblocker: like Adblock or uBlock origin (even better, IMO) .

Sounds like a lot, maybe, but those pests are ubiquitous and highly invasive, so they deserve this.


> **xenon3 said:**
>  
[LIST=1]
[*]Can an UBUNTU system also be awaken on LAN? 
[/LIST]


I think so, but only if you enable this somewhere: not by default, that I know of.

---

### Post by &amp;KyT$0P# on 2016-08-27
> **HermanAB said:**
> I find Ghostery to be quite a bit more convenient than Noscript
Ghostery is a totally different thing from NoScript - privacy extension with blacklist subscription vs security extension with user-controlled lists.  This site is an ad server so whether Ghostery helps or not totally depends on whether they think it's a tracker, not what you decide you need or want to block.

> **coldraven said:**
> I run NoScript **and** Ghostery!
Well Ghostery is known not to play nice with other extensions - including NoScript - so doing that is a bad idea unless you're like coldraven an advanced user who knows how to spot and troubleshoot such conflicts.

For everyone else who wants to use NoScript plus such an extension, uBlock Origin is a better alternative for privacy protection.

---

