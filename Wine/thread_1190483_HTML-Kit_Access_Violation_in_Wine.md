---
title: "HTML-Kit Access Violation in Wine"
date: 2009-06-17
forum: Wine
---

### Post by MrLeN on 2009-06-17
I have wine installed and I have HTML-Kit installed, and it loads up fine and I can use it fine, but when I go to Preferences and try to change the options, I get "Access Violation 0000000000". So, I can't change the preferences (which I need to change).

I want to try and work out any problems with using HTML-Kit and wine, because I've gone through all the other Linux editors, many times over the last several years, and there is honestly none that do what HTML-Kit does "for me", and the way I use it.

So, I will bend over backwards to get HTML-Kit working. The fact that I am willing to try SO hard to get this working is a testament to how much I really don't want to use the other editors. All the editors are fine for one thing or another, but for my purposes and the way I hand code, I must use HTML-Kit. End of story. I just must. 

Please don't turn this into a discussion about what else I could or couldn't be using. I've been there, done that. I'm off it. I don't mean to go on, but such threats always take that route.

Keep in mind that this thread will also eventually show in search engines, so maybe in 6 weeks or even 6 months, someone will come across this thread and somehow I might benefit from that. I am prepared to wait that long, because I MUST have HTML-Kit.

So, All I want to know for now is -- Does anyone have any suggestions as to why I am getting an access violation. I figured that because preferences must obviously save some setting to a file somewhere, that it might be privileges, considering that Ubuntu is Linux. So, I just went and gave read and write privileges to the entire HTML-Kit folder in wine. That didn't solve the problem.

Any other suggestions?

---

### Post by NightMKoder on 2009-06-17
Doesn't look like anyone takes care of it in wine. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=461](http://appdb.winehq.org/objectManager.php?sClass=application&iId=461) . Apply to become a maintainer, compile wine, file bugs (with logs), etc.

---

### Post by MrLeN on 2009-06-18
> **NightMKoder said:**
> Doesn't look like anyone takes care of it in wine. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=461](http://appdb.winehq.org/objectManager.php?sClass=application&iId=461) . Apply to become a maintainer, compile wine, file bugs (with logs), etc.

That's all well and good, but I donno how.

If I knew how, I'd just fix it and not post this thread :(

---

### Post by qwertymn on 2009-06-19
try 'winetricks cc580'
that will get you past the bug

---

