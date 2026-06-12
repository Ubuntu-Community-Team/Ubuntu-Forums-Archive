---
title: "Do I have scareware on my system?"
date: 2012-01-28
forum: Security
---

### Post by zozza on 2012-01-28
Hi, 

A few days ago I was browsing a website.  I am using 10.04 and Firefox 9.01.

I sent the link of a particular page to a friend of mine who was using XP.

Immediately, he lost his connection and within a few seconds "scareware" popped up telling him that his computer had loads of errors, etc, and he needed to pay $85 to get the (fake) anti-virus which also downloaded to work and solve the problem.

His AV revealed that he had downloaded the Hiloti trojan which, from what I understand, can be bundled with a large number of malware and scareware products. 

I assume (but I do not know) that a combination of Ubuntu and Firefox (always upgraded) meant that I have not been infected.  There are no overt signs.  

However, I do not know that my system is clean.  What is the best tool to detect if there is anything nasty on my system.

Also, is it a reasonable assumption to state that because I am using Ubuntu I am - at least in the situation described - safe?

Thanks!

---

### Post by sudodus on 2012-01-28
No linux is not immune to attacks, but the threat is somewhat different compared to Windows (and probably smaller because many hackers target the most wide-spread operating system). Read the following wiki page to get started
[[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by OpSecShellshock on 2012-01-28
Unfortunately there's nothing that you would be able to use to check for that type of malware on your machine, but in this case it's unlikely you got anything. If you had a fake AV you'd be getting the same kinds of warnings and suggestions to buy the software. The link probably just went to a site that had been compromised to redirect to malware, but only for Windows.

You won't be able to know 100% that you didn't get anything unless you do a full clean install, but only because you can't prove a negative. It is highly unlikely that the malware had a Linux version. For the sake of being precise: your Ubuntu system can't run or install malware that was specifically written for Windows, but that's the only sense in which you are safe using Ubuntu.

---

