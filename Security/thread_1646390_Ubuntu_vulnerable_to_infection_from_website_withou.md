---
title: "Ubuntu vulnerable to infection from website without a &quot;proxy antivirus filter&quot;?"
date: 2010-12-15
forum: Security
---

### Post by nrundy on 2010-12-15
I used Avast webfilter (proxied webtraffic through Avast) when running Windows. Sometimes Avast would alert and "protect" me from being infected by a compromised website. NOTE: Avast would alert even absent clicking any links. Just viewing the page could result in infection.  Should I be running some kind of proxy webfilter for protection? My understanding is that Firefox can be compromised and this can in turn compromise Ubuntu. Are these kinds of threats specific to Windows running Firefox, or Firefox per se. If Firefox per se it seems like I need some sort of Proxy webfiltering like Avast provides.

---

### Post by OpSecShellshock on 2010-12-15
It shouldn't be necessary. Web-based malicious code is almost exclusively written for Windows systems. There aren't any known variants that would affect Linux desktop. A third party proxy/filter would prevent such things from executing (provided it knows about them beforehand), but it wouldn't really be necessary if you aren't on the OS that they target. If anything did happen in Firefox, all you'd need to do is delete your profile and start another one.

In any case, using the NoScript add-on in Firefox would accomplish the same thing on your local machine.

---

### Post by nrundy on 2010-12-15
I just returned to the zencast page using Windows and Avast alerted again. It was .../images/rvmlogobug.jpg. I didn't post whole address cause I don't want anyone to get infected. I run NoScript but I would assume ZenCast to be a safe site. So would have been likely to at least temporarily disable NoScript for this site.   Would this leave Ubuntu vulnerable without a WebShield/filter?

---

### Post by CharlesA on 2010-12-15
What is the exact error you are getting from Avast? If you use NoScript and AppArmor, you should be fine.

---

### Post by DodgeV83 on 2010-12-15
Enable the AppArmor profile for Firefox and you should be fine.

---

### Post by nrundy on 2010-12-16
> **CharlesA said:**
> What is the exact error you are getting from Avast? If you use NoScript and AppArmor, you should be fine.

 Even if I temp allow NoScript on the page, I'll be safe with this AppArmor thing? But absent AppArmor, I might have a problem? As my previous post states, I would assume this is a legit safe site if Avast wasn't alerting.

---

### Post by communityofexcellence on 2010-12-16
One thing you should also try to do is contact the administrator of the site if you feel it's safe and find out what's the deal.

---

### Post by OpSecShellshock on 2010-12-16
Legitimate sites do get compromised from time to time. Generally when that happens, though, they are set up so that they will try to load content from other domains entirely without users/browsers/administrators being aware that it's happening. In those cases, even allowing the main site in NoScript should be reasonably safe because the site that the malicious content is being loaded from still hasn't been allowed. However, if the compromised site contains the malicious code locally, then it would execute if the domain is allowed.

---

### Post by nrundy on 2010-12-16
I just recently read on arstechnica.com about ad exploits being planted on legitimate sites and it takes a while before site operator learns what's happening. People were infected by just visiting the site even without clicking a link. 

I'll send word to ZenCast about Avast's alerts.

---

### Post by bodhi.zazen on 2010-12-16
> **nrundy said:**
> I used Avast webfilter (proxied webtraffic through Avast) when running Windows. Sometimes Avast would alert and "protect" me from being infected by a compromised website. NOTE: Avast would alert even absent clicking any links. Just viewing the page could result in infection.  Should I be running some kind of proxy webfilter for protection? My understanding is that Firefox can be compromised and this can in turn compromise Ubuntu. Are these kinds of threats specific to Windows running Firefox, or Firefox per se. If Firefox per se it seems like I need some sort of Proxy webfiltering like Avast provides.

Although nothing is impossible, it is highly unlikely simply loading a web page will affect Ubuntu.

If such a thing happened it would be a flaw in firefox, javascript, of flash and the vulnerability would then need to target Linux.

If you would like to increase your browser security see:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

