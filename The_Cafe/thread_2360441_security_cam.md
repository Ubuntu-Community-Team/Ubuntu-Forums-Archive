---
title: "security cam"
date: 2017-05-04
forum: The Cafe
---

### Post by nonparity on 2017-05-04
I would like to install some security cameras around my house. I am looking for wifi connected and motion activated that would connect to a nas device, computer(that is running Ubuntu of course), or a cloud service for storing the video. Any recommendations?

---

### Post by TheFu on 2017-05-04
Recommend searching for the model and "hacked" before purchase.  Think pretty much all of these cameras have been hacked, especially with wifi models.  Most of the names you already know are in the 'hacked' list.

If I were in the market, I'd look for a PoE camera. Only 1 line run this way and it can be put onto a different vlan from everything on the network to limit unwanted viewers.  Also, don't use any "cloud-based" apps for the cameras. 
[https://www.ifsecglobal.com/how-to-hack-a-security-camera/](https://www.ifsecglobal.com/how-to-hack-a-security-camera/)
[http://abcnews.go.com/WNT/video/home-security-cameras-hacked-streamed-live-online-45602066](http://abcnews.go.com/WNT/video/home-security-cameras-hacked-streamed-live-online-45602066)
[http://www.pcmag.com/news/351120/samsung-security-cameras-hacked-again](http://www.pcmag.com/news/351120/samsung-security-cameras-hacked-again)
[http://www.citynews.ca/2016/08/11/dozens-of-security-cameras-exposed-by-hacker-app/](http://www.citynews.ca/2016/08/11/dozens-of-security-cameras-exposed-by-hacker-app/)
[http://www.firstcoastnews.com/news/wireless-camera-hacking-leaves-st-augustine-family-feeling-unsecure/384901995](http://www.firstcoastnews.com/news/wireless-camera-hacking-leaves-st-augustine-family-feeling-unsecure/384901995)

Don't use any cloud stuff for this, especially, not for this.

---

### Post by nonparity on 2017-05-04
thefu good idea on searching for hacked with the model and thanks for the links too

---

### Post by TheFu on 2017-05-04
Be certain the firmware is newer than Feb 2017.  Prior to that there was a nasty Linux kernel bug across all Linux systems (except redhat).  
That means every desktop, server, camera, android device, router, switch, webcam, media player, TV, whatever, running Linux needs a newer kernel if it was networked.  It was a very serious remote execution (takeover) bug.

---

### Post by CharlesA on 2017-05-06
> **TheFu said:**
> Be certain the firmware is newer than Feb 2017.  Prior to that there was a nasty Linux kernel bug across all Linux systems (except redhat).  
That means every desktop, server, camera, android device, router, switch, webcam, media player, TV, whatever, running Linux needs a newer kernel if it was networked.  It was a very serious remote execution (takeover) bug.

Are you talking about the ["Dirty Cow"]("https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5195") bug?

---

### Post by TheFu on 2017-05-06
No.
[http://www.securityfocus.com/bid/97397](http://www.securityfocus.com/bid/97397) This bug was patched and should have been updated to orgs doing monthly patching BEFORE it was announced.  2.6x. --> 4.4.x impacted.

---

### Post by litlesam on 2017-05-06
> **TheFu said:**
> No.
[http://www.securityfocus.com/bid/97397](http://www.securityfocus.com/bid/97397) This bug was patched and should have been updated to orgs doing monthly patching BEFORE it was announced.  2.6x. --> 4.4.x impacted.

Thanks for the link.

---

### Post by CharlesA on 2017-05-06
> **TheFu said:**
> No.
[http://www.securityfocus.com/bid/97397](http://www.securityfocus.com/bid/97397) This bug was patched and should have been updated to orgs doing monthly patching BEFORE it was announced.  2.6x. --> 4.4.x impacted.

That sounds nasty. Thanks for the link!

---

