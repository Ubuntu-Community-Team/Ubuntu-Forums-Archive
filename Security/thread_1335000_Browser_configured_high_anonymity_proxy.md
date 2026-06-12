---
title: "Browser configured high anonymity proxy?"
date: 2009-11-23
forum: Security
---

### Post by dillandriskell on 2009-11-23
Hi

I'm looking for a high anonymity proxy, meaning one that doesn't identify itself as a proxy server and doesn't make available the original IP address.  I'm looking for perhaps open-source Linux software that maybe you guys have had good luck with, or perhaps an add-on for Firefox that's done well for some of you?  Any information would be very much appreciated, I've had some trouble finding either the software or information on it.

EDIT: I'm also looking for more than just a web based proxy, something I could preferably turn on and off.

---

### Post by wilee-nilee on 2009-11-23
Tor is a pretty good one but true anonymity is impossible, at least for a regular user.

---

### Post by scorp123 on 2009-11-23
*Hmmmm .... Opera with the "Turbo" thing enabled?*  <=== EDIT: Forget it. It's not correct and "Turbo" will still reveal your real IP. Please ignore what I wrote. Sorry about that.

---

### Post by wilee-nilee on 2009-11-23
> **scorp123 said:**
> Hmmmm .... Opera with the "Turbo" thing enabled? That's basically an anonymous proxy right there built into the browser. Not open-source, I know. But it's good and it works. Maybe you want to try that?

[http://wapreview.com/blog/?p=2984](http://wapreview.com/blog/?p=2984)

With Opera "Turbo" turned on you're basically behind Opera's proxies in Norway and nobody can get your real IP.

[http://www.youtube.com/watch?v=-xo-oQIxyJM](http://www.youtube.com/watch?v=-xo-oQIxyJM)

Opera turbo is very problematic. A true proxy that would provide anonymity would have to be a computer on a network that has a different IP before it hits the 1st server.

Your information is completely wrong I just ran a whats my IP and it showed the same IP with FF and Opera Turbo.

---

### Post by dillandriskell on 2009-11-23
Tor looks like it'll work great for me.  I'm messing with it right now, thank you wilee-nilee.  

Unfortunately I don't think I could commit to another browser just for web security though, and I'd prefer to stick with Firefox, thank you though scorp.

Hmm...another concern of mine.  Do I need to worry about masking my OS or Web Browser?  Or does Tor do that for me when it blocks javascript and such?

---

### Post by scorp123 on 2009-11-23
> **wilee-nilee said:**
>  Your information is completely wrong I just ran a whats my IP and it showed the same IP with FF and Opera Turbo. Oh dear ... you're right. My bad.

I'm going to change my posting up there ...

---

### Post by wilee-nilee on 2009-11-23
Actually Tor suggests a single browser for their proxy and opera is a good one especially the latest seems to be running at light speed. It is a easy set up to have opera be a proxy only browser. The tor toggle is a pain in The booty in FF.

---

### Post by wilee-nilee on 2009-11-23
> **scorp123 said:**
> Oh dear ... you're right. My bad.

I'm going to change my posting up there ...

I new you meant well but the only way to check if your really at least at the end of the last server is with a whats my IP or the Am I Using Tor with using Tor.

Proxies are problematic if it is bounced in you own country it leaves a trace on the web, and from your computer to the first proxy is open, unless encrypted. proxies are really only good for not showing your IP to the final destination. Although there are stronger proxy setups for the government security agencies, for us regular user it is mainly not showing the correct IP to the destination.

---

### Post by scorp123 on 2009-11-23
> **wilee-nilee said:**
> I new you meant well but the only way to check if your really at least at the end of the last server is with a whats my IP or the Am I Using Tor with using Tor. Well, with Opera Mobile you pass through the same proxies and there you indeed get their Norwegian addresses. But I guess this has to do with the fact that most mobile/3G providers give 10.0.0.0 addresses to their customers (e.g. I indeed get a RFC1918 private range address from my providers here when I connect with my 3G USB-stick or phone) and the official IP is somewhere further up ... I assumed that desktop Opera would work the same. OK ... I was wrong. Sorry about that.

---

### Post by Sarmacid on 2009-11-23
> **wilee-nilee said:**
> The tor toggle is a pain in The booty in FF.It's actually really easy, unless 1 click is a pain in the booty for you :P

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

As for browser/os anonymity I'm not sure how it's done, but one of the things I would consider is getting the FF add-on user agent switcher.

---

### Post by wilee-nilee on 2009-11-23
> **Sarmacid said:**
> It's actually really easy, unless 1 click is a pain in the booty for you :P

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

As for browser/os anonymity I'm not sure how it's done, but one of the things I would consider is getting the FF add-on user agent switcher.

One click thats just to much work,;) actually I had some troubles with toggling to adjust the set up which had the tor gui popping up every time I tried to close it after adjusting it and it was the toggle on toggle off which was the key point, sometimes I miss the obvious. ;)

---

### Post by dillandriskell on 2009-11-26
Alright, thanks for all the responses guys.  Sorry for the delay, when I went to go install tor I messed something up pretty bad but I've fixed it, was all me though :oops:.  Anyways my questions have been answered so again, thank you.

---

