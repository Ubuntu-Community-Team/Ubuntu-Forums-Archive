---
title: "Ransom32 and Linux?"
date: 2016-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Gottier on 2016-01-07
So, there's plenty of news articles in the last few days about ransom32, a ransomware type malware, and these articles all suggest that Linux is vulnerable. Lately I have noticed that when I'm using Chrome or Firefox that sometimes I get a never-ending popup type thing going on, and the only way I can stop it is to kill Chrome or Firefox. I'm just wondering if this ransom32 is the same sort of thing, but turns out to be a full blown virus.

I tried to search this forum for "ransom32" and found nothing, so apparently it's not an active problem with Ubuntu users. I'm curious about this. Anyone know anything about it, how it relates to us Ubuntu users, what we can/should do to stay safe?

---

### Post by matt_symes on 2016-01-07
Looks like it affects Chromium and Chrome. I use Firefox.

From what I've just read, I can't understand how the developers didn't see this coming. I want my browser to have less control on my system, not more.

An AppArmor profile would nail this one or a VM for browsing.

---

### Post by coldraven on 2016-01-07
The most effective solution for any OS is to back-up your data to an external drive and then unplug it. If by some fluke you do get infected just do a re-install and this time remove Adobe Flash permanently.

---

### Post by buzzingrobot on 2016-01-07
It's malware not a virus.  It's not an in-browser Javascript exploit.  Could be packaged to target Linux but, apparently, no one has evidence that it has been.

Be careful where you phish.

More here: [URL="http://blog.emsisoft.com/2016/01/01/meet-ransom32-the-first-javascript-ransomware/"]http://blog.emsisoft.com/2016/01/01/meet-ransom32-the-first-javascript-ransomware/


[/URL]

---

### Post by Gottier on 2016-01-07
> **buzzingrobot said:**
> 
More here: [URL="http://blog.emsisoft.com/2016/01/01/meet-ransom32-the-first-javascript-ransomware/"]http://blog.emsisoft.com/2016/01/01/meet-ransom32-the-first-javascript-ransomware/
[/URL]

Based on the webpage and comments, it's hard to say whether or not Linux users would have a problem unless they intentionally installed a .deb, true? It sounds like this isn't something you get while browsing the internet, just by stumbling on an infected website.

---

### Post by buzzingrobot on 2016-01-07
If someone packaged it for Linux, as they have for Windows, I don't think it would need to be as a deb or an rpm, so long as it put its files where it wanted.

---

