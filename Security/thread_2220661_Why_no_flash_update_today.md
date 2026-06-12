---
title: "Why no flash update today?"
date: 2014-04-28
forum: Security
---

### Post by estamets on 2014-04-28
[http://helpx.adobe.com/security/products/flash-player/apsb14-13.html](http://helpx.adobe.com/security/products/flash-player/apsb14-13.html)

We should be at 11.2.356. 

These were updated today:
[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

Is it because it's a level 3 priority which is "adminstrator discretion"? Just curious if that's the case.. Or if they need to take a peek at what's going on and repackage it or whatnot?

---

### Post by WogBoy on 2014-04-29
I guess they forgot the update for linux.

**Zero-day Flash bug under active attack in Windows threatens OS X, Linux too**

[http://arstechnica.com/security/2014/04/windows-0day-flash-bug-under-active-attack-threatens-os-x-linux-too/](http://arstechnica.com/security/2014/04/windows-0day-flash-bug-under-active-attack-threatens-os-x-linux-too/)

---

### Post by Danny_Barbz on 2014-04-29
> **WogBoy said:**
> I guess they forgot the update for linux.


What else is new?

---

### Post by bashiergui on 2014-04-29
It's listed as priority 3 on Linux > This update resolves vulnerabilities in a product that has historically not been a target for attackers. Adobe recommends administrators install the update at their discretion.
[http://helpx.adobe.com/security/severity-ratings.html](http://helpx.adobe.com/security/severity-ratings.html)

i'd read that to mean they focused on releasing the patch for systems actively being exploited (windows). I'd expect the linux update to come later.

---

### Post by bashiergui on 2014-04-29
> **WogBoy said:**
> **Zero-day Flash bug under active attack in Windows threatens OS X, Linux too**

[http://arstechnica.com/security/2014/04/windows-0day-flash-bug-under-active-attack-threatens-os-x-linux-too/](http://arstechnica.com/security/2014/04/windows-0day-flash-bug-under-active-attack-threatens-os-x-linux-too/)
Wow that article is a confuddled mess. The author hasn't grasped the difference between the two identified attacks.
 [Cve-2014-1776]("http://www.fireeye.com/blog/uncategorized/2014/04/new-zero-day-exploit-targeting-internet-explorer-versions-9-through-11-identified-in-targeted-attacks.html") is the Internet Explorer vuln, not the[ flash]("https://www.securelist.com/en/blog/8212/New_Flash_Player_0_day_CVE_2014_0515_used_in_watering_hole_attacks") one. A flash exploit is used in both attacks, one was an old vuln that had a patched released last year.

---

### Post by claracc on 2014-04-30
I have just received today the flashplayer plugin update for my 12.04 ubuntu. See atached image.

---

### Post by monkeybrain20122 on 2014-04-30
I got the update in 14.04 and 13.10 earlier this afternoon/evening (no sure exactly when but when it was upgraded). I am wondering what will happen to Chrome and pepper flash...  Was there a Chrome update?

---

### Post by vasa1 on 2014-04-30
> **monkeybrain20122 said:**
> I got the update in 14.04 and 13.10 earlier this afternoon/evening (no sure exactly when but when it was upgraded). I am wondering what will happen to Chrome and pepper flash...  Was there a Chrome update?

There was one on the 24th: [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/). They're always updating ;)

---

### Post by estamets on 2014-04-30
> **bashiergui said:**
> Wow that article is a confuddled mess. The author hasn't grasped the difference between the two identified attacks.
 [Cve-2014-1776]("http://www.fireeye.com/blog/uncategorized/2014/04/new-zero-day-exploit-targeting-internet-explorer-versions-9-through-11-identified-in-targeted-attacks.html") is the Internet Explorer vuln, not the[ flash]("https://www.securelist.com/en/blog/8212/New_Flash_Player_0_day_CVE_2014_0515_used_in_watering_hole_attacks") one. A flash exploit is used in both attacks, one was an old vuln that had a patched released last year.

I'm glad I'm not the only one who thought it. I'm thinking to myself a few days ago that what I read didn't make sense. I also read that disabling flash in IE and then to use a different browser. Errr.. I was very confused. 

I did get the update when I got home from work the next day. We're all good. 

Here's the bigger question I have though. In the flash case. Is it better to take a version and patch the crap out of it or is it better to get new? I know we linux folks have another 3 years? on 11.2.

---

### Post by bashiergui on 2014-04-30
> **estamets said:**
> Here's the bigger question I have though. In the flash case. Is it better to take a version and patch the crap out of it or is it better to get new? I know we linux folks have another 3 years? on 11.2.
Not sure what you mean. If you installed flash brand new today, it would be the fully patched version. If you have updated your existing flash, then you have that same fully patched version.

flash is still getting updated for a few more years, no reason to bail yet.

---

