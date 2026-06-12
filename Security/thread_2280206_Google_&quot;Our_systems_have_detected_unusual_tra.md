---
title: "Google: &quot;Our systems have detected unusual traffic from your computer network.&quot;"
date: 2015-05-28
forum: Security
---

### Post by VMC on 2015-05-28
I just started getting these messages using google search engine, I need to use captcha for the search to continue. The "Best answer: from google doesn't work. No malware. I use different OS's - windows, two linuxes, etc.

This just started. Anyone else have this issue?

Here's a link to fix the problem:
[https://support.google.com/websearch/answer/86640?rd=1](https://support.google.com/websearch/answer/86640?rd=1)

---

### Post by tgalati4 on 2015-05-28
No problem using google search using google chrome.  I'm in So Cal as well.  Perhaps you have a tracker or other malware in your browser.  Try clearing your cache and if that doesn't work, the delete your profile.

---

### Post by vasa1 on 2015-05-29
> **VMC said:**
> I just started getting these messages using google search engine, I need to use captcha for the search to continue. ...
I think I had something similar a long time ago. It happened when I used the "date" (?) option to search specifically for something I had posted a long time ago. I thought I could narrow things down but looks like Google got a bit suspicious. (Mostly, I find what I want in the first few hits on the first page itself.)

Do you have the problem with incognito mode or when using another Google account?

---

### Post by VMC on 2015-05-29
Thanks for the reply. This happens on both Chrome on Windows 8, and Firefox on two different Ubuntu's. Since they don't share the same cache I don't think that's the issue.

---

### Post by Bucky Ball on 2015-05-29
I get exactly the same thing using Google scholar occasionally. I just fill in the captcha and continue. Sometimes it give me another captcha, and one time another, but I get there eventually.

It usually only happens to me for a short amount of time, then the captcha requirement with Google scholar disappears and everything is back to normal again. Hasn't happened for about five months.

---

### Post by QDR06VV9 on 2015-05-29
I used to do a little NetNanny help, and have been asked again to volunteer my time.
But some of the links i was asked to check were always met with a captcha.
Not knowing what the links would do or take me I found a spoofing agent for firefox witch would mask what ever I wanted
> Rotates complete browser profiles ( from real browsers / devices ) at a  user defined time interval. It includes many extra privacy enhancing  options
I was always behind a VPN and a Proxy though!
Worth a look [https://addons.mozilla.org/EN-us/firefox/addon/random-agent-spoofer/](https://addons.mozilla.org/EN-us/firefox/addon/random-agent-spoofer/)

---

### Post by VMC on 2015-05-29
I found the problem!

It was in Windows 8, Chrome settings: ~/AptData/Local/Google/Chrome/User Data/Default files.
A malware program found 155 threats in "Web Data", and "Sync Extension Settings". I just deleted all those and reset Chrome to default settings.
I had the use captcha one last time. Now it appears to be fixed.

I found it by just observing the network activity. I saw a flash of akamitecnologies web access. Further analysis led me to a virus/malware associated  with that web access. I think akamitecnologies may be okay, but the malware was somehow piggybacked on it. At anyrate, its solved.

---

### Post by levan3 on 2016-04-25
Hi guys. Does anyone knows what kind of traffic google considered as unusual?

---

### Post by oldos2er on 2016-04-25
Old thread closed.

@levan3, not sure your question is answerable in ubuntuforums, but you can try starting a new thread for it in the Cafe.

---

