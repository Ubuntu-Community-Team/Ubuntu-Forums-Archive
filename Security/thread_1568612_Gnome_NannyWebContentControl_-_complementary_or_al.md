---
title: "Gnome Nanny/WebContentControl - complementary or alternatives?"
date: 2010-09-05
forum: Security
---

### Post by daboochmeister on 2010-09-05
I understand WebContentControl in some detail -- but am now reading about Gnome Nanny, without really understanding its architecture, etc.

So ... is Gnome Nanny an alternative to WebContentControl, or does it make sense to run both?

So far, from what i can find, I'm inferring that Gnome Nanny filters access based on a blacklist, and limits times when the web can be accessed (both of which you can do with WebContentControl, with some advanced configuration).  But does it do more than that, e.g., the more advanced DansGuardian kind of parsing for phrases, looking for proxy references, etc.?

tia!

---

### Post by wacky_sung on 2010-09-06
Web filter - You can choose [privoxy]("https://help.ubuntu.com/community/Privoxy") which is good in filtering all those ads and work very effective.You can control also those sites in which you wanna block it as well.

My personal rating for Privoxy = 95% (some sites may not be working very well such as facebook)

Parent guardian(for parent) - You can use [dansguardian]("https://help.ubuntu.com/community/Servers/DansGuardian") which is very good and even i have test it with proxy which work well to block it also.

My personal rating for Dansguardian = 99.99% (Working so far so good but it may get bypass through some cgi proxy online)

---

