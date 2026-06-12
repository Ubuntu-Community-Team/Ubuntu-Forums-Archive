---
title: "Safety Precautions for Using a Web Browser"
date: 2024-09-13
forum: Security
---

### Post by netw844f on 2024-09-13
I've been using my web browser (Firefox, specifically) to view and navigate through personal files like PDFs, images, and videos stored on my computer. I'm wondering if this is a risky practice or something I should be concerned about. What precautions should I be taking?

I have a couple of specific questions:

1-Is there any chance that my browser could send what I'm viewing on my local webpages to anyone on the internet?

2-Could Mozilla or any third parties potentially access or see my documents through some kind of security leak?

I keep my browser up to date and I've customized the 'Privacy & Security' settings. For instance, I've set Enhanced Tracking Protection to 'Custom', enabled 'Tell websites not to sell or share my data', and turned on 'Send websites a "Do Not Track" request', among other tweaks.

Do you think these measures are sufficient? I've also been considering using a dedicated browser just for viewing my local files - something like LibreWolf or Pale Moon. Is it a good idea?

Thank you

---

### Post by werewulf75 on 2024-09-13
> **netw844f said:**
> I've been using my web browser (Firefox, specifically) to view and navigate through personal files like PDFs, images, and videos stored on my computer. I'm wondering if this is a risky practice or something I should be concerned about. What precautions should I be taking?
Risky as such, no, unless your browser has fallen victim to some kind of malware or other. But as you're only viewing local files, you could always disconnect from network/internet and work offline, just for added comfort. Also, even in 'Always Private' mode, recent-ish versions of Firefox don't delete all cached data/files when you exit the program so it's good practice to manually delete everything inc. all history before closing the browser, and if you're really paranoid - I am! ;) - do the same again when starting/re-starting FF.  
> **netw844f said:**
> I have a couple of specific questions:

1-Is there any chance that my browser could send what I'm viewing on my local webpages to anyone on the internet?
Virtually zero chance, unless some kind of malware is operating and even then, remote chance.
> **netw844f said:**
> 2-Could Mozilla or any third parties potentially access or see my documents through some kind of security leak?Mozilla isn't anything to worry about - if there was anything in the code to facilitate this we'd know about it pretty quickly. :) However, third parties can't be entirely discounted, but then if you're working offline, nothing can go out.
> **netw844f said:**
> I keep my browser up to date and I've customized the 'Privacy & Security' settings. For instance, I've set Enhanced Tracking Protection to 'Custom', enabled 'Tell websites not to sell or share my data', and turned on 'Send websites a "Do Not Track" request', among other tweaks.

Do you think these measures are sufficient? I've also been considering using a dedicated browser just for viewing my local files - something like LibreWolf or Pale Moon. Is it a good idea?

Thank you
Firefox is fast falling out of favour with me, what with the settings now including an "option" to send advertisers all kinds of data albeit 'anonymised'. Most of my browsing takes place in TOR browser but I'm now trying out various other privacy browsers to replace FF. You may well prefer to switch to something like Librewolf or Pale Moon for general use.

---

### Post by netw844f on 2024-11-20
Thank you for your helpful answer

---

### Post by netw844f on 2024-11-20
What is your experience with these browsers? I will test these three browser suggestions:

[https://www.torproject.org/](https://www.torproject.org/)

[https://librewolf.net/](https://librewolf.net/)

[https://www.palemoon.org/](https://www.palemoon.org/)

---

### Post by TheFu on 2024-11-20
> **netw844f said:**
> 
1-Is there any chance that my browser could send what I'm viewing on my local webpages to anyone on the internet?

**Any chance**?  Sure.  Every time you allow javascript to run, you've allowed the stuff in that specific website/page to be accessed and handled in any way that javascript can handle.  That can easily include uploading it to some website.  Addons/extrensions allowed to run in the browser can do this as well.  Mozilla warns against using random addons for good reason.  It applies to all addons/extensions to any browser. Beware.

OTOH, does it happen constantly?  Who knows?  There's so much happening with network receipts and sending that without an application firewall or wireshark capture, you'll likely never know

> **netw844f said:**
> 
2-Could Mozilla or any third parties potentially access or see my documents through some kind of security leak?

Yes.  Mozilla probably has little interest, since there are ways they could get as much data as they like from you already. You are running their code on your computer after all.  There's a point where worrying about what's possible and sticking with what's likely is better for your happiness. We each have different risks and levels of hassle we are willing to deal with.  Mozilla has a reputation to protect, which is the main reason I'm willing to trust them.  They know there are other browsers and that people will happily switch if they do anything bad, so they wouldn't get the search-engine kickbacks that fund much of their company.

> **netw844f said:**
> 
I keep my browser up to date and I've customized the 'Privacy & Security' settings. For instance, I've set Enhanced Tracking Protection to 'Custom', enabled 'Tell websites not to sell or share my data', and turned on 'Send websites a "Do Not Track" request', among other tweaks.

To my knowledge, no websites actually pay attention to "do not sell or share my data" or "Do not track" requests. Those are options we all set and we feel better with them, but .... 

> **netw844f said:**
> 
Do you think these measures are sufficient? I've also been considering using a dedicated browser just for viewing my local files - something like LibreWolf or Pale Moon. Is it a good idea?

I use 4 different browsers for different purposes.  Usually they are run inside a constrained environment or a touch-no-local disk environment if I want no trace on the computer.  Of course, my DNS provider and ISP know where and when I've been if I'm not running a VPN. If I run a VPN, then the VPN host and hosting company knows these things, but probably can't tie my location to where the VPN traffic is really headed.  This assums they aren't doing deep packet inspection, which has been around for over 2 decades now and CAN tied inbound traffic to outbound traffic. In the early 2000s, only Govts and Fortune 10 company did Deep Packet Inspection due to the costs involved, but that has become easier and easier over all this time, making it much more available even to mid-sized companies and small security firms.

---

### Post by werewulf75 on 2024-11-22
> **netw844f said:**
> What is your experience with these browsers? I will test these three browser suggestions:

[https://www.torproject.org/](https://www.torproject.org/)

[https://librewolf.net/](https://librewolf.net/)

[https://www.palemoon.org/](https://www.palemoon.org/)
Out of *all* browsers, TOR is by far the most  secure and private one. I have used it for the majority of my web activity for years.

Pale Moon's web site seems to have been down lately and only come back in the last few days. I have it now installed on Windows 10, Ubuntu 22.04, and Ubuntu 20.04. Too early to fully comment but first impressions, seems OK. Website poor, not sufficiently informative. 

LibreWolf, also a bit of a recent addition on Ubuntu 22.04 and Fedora 40. Really very poor website. Browser again, OK so far.

On the whole, going by early impressions, I prefer Waterfox to the last two.

---

