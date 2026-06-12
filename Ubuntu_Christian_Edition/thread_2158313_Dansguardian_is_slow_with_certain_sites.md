---
title: "Dansguardian is slow with certain sites"
date: 2013-06-28
forum: Ubuntu Christian Edition
---

### Post by Azrael84 on 2013-06-28
For example maps.google.co.uk. This wasn't the case until a few weeks ago, what could have changed?

Dasngurdian is fast with the rest of google, and even fast with maps.google.co.uk when it finally loads after several minutes.
As soon as Dasnguardian is removed from the equation, and firefox is pointed straight through the proxy (privoxy) maps.google.co.uk is
fast again, so I know it is DG slowing things.

I've tried monitoring the logs with loglevel=3, logexceptionhits = 2, reportinglevel = 2 set but see nothing being DENIED. I've
also added maps.google.co.uk, gstatic.com, googleapis.com, mts0.google.com, mts1.google.com, apis.google.com, googleusercontent.com
to "exceptionsitelist". Still no change.

Could anyone point me in the right direction here? Would be nice to figure this out as it may help in the future with other slow sites
behaving in this way.

---

### Post by jaimerosario on 2013-12-27
Did you checked "exceptionregexpurllist" and "bannedregexpurllist"?

Some time ago, a missing special character like "(" , ")", or "|", I don't remember now, but put my Dansguardian very slow.

---

### Post by Azrael84 on 2013-12-27
Interesting.....I guess I could give it a go with the minimal stripped down lists, and see if that gets rid of the slowness then gradually add the entries back one by one to find if one is the problem. Thanks..

---

