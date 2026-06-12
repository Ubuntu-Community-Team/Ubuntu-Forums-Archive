---
title: "Firefox updates may alter your preferences"
date: 2016-12-05
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-12-05
I just came across [Beware! Firefox updates may reset preferences]("http://www.ghacks.net/2016/12/05/beware-firefox-updates-may-reset-preferences/")

The author mentions feedback from two users and that he could confirm the reset. So if your Firefox is somewhat different after an update (excluding what's mentioned in the release notes) you may need to go back in and set things back to the way they were if that's possible (and desirable).

---

### Post by &amp;KyT$0P# on 2016-12-05
Yet another reason why you should **always** back up your Firefox [profile]("http://kb.mozillazine.org/Profile") **before** changing Firefox versions.  It's easy to completely quit Firefox, then copy [FONT=Courier New]~/.mozilla/firefox[/FONT] somewhere safe.

In this case, that backup could be used for diff of [prefs.js]("http://kb.mozillazine.org/Prefs.js_file").  I wouldn't restore the old [FONT=Courier New]prefs.js[/FONT] wholesale here, as Firefox will then pick up the previous Firefox version and likely reset stuff all over again.

---

### Post by mikodo on 2016-12-05
Thanks folks.

 I had never looked into my prefs.js before today. As, I have been bringing my 'defaults' from backups, to new installs for a long time now, when I started looking today at my prefs.js, I found stuff in it I had deleted years ago. One was the now 'infamous' WOT. When I went into about:config, there were two entries for it there. Now, I know to remove stuff in there too.

I couldn't see any changes, that FF had made during recent updates in 'Preferences', nor changes I had made in 'about:config'. So, I am good with those being as I had set them before the updates, since I last checked. Lucky, I guess.

Live and learn. 

Thank goodness for open-source software. FF let's go in and change things to our liking.

---

### Post by neothethird on 2016-12-06
Does that also happen with Sync enabled? I guess not, since i never had any problems.

---

