---
title: "Firefox 35 still stuck in &quot;Proposed&quot;?"
date: 2015-01-26
forum: Ubuntu Development Version
---

### Post by Ian_Worrall on 2015-01-26
Anyone know when it'll be pushed across to main?

(Unwilling to enable proposed, worried about breakage)

---

### Post by xc3RnbFO8P on 2015-01-26
strange I got Firefox 36

---

### Post by harry332 on 2015-01-26
Well firefox v. 35 is no longer available in vivid-proposed.
And v. 34 is in main.
Instead firefox 36 beta2 is now available in vivid-proposed.

---

### Post by raptir on 2015-02-24
I noticed this is still the case. No 35 in Vivid, even though Utopic has been bumped up to 35.

---

### Post by sammiev on 2015-02-24
> **harry332 said:**
> Well firefox v. 35 is no longer available in vivid-proposed.
And v. 34 is in main.
Instead firefox 36 beta2 is now available in vivid-proposed.

+1

---

### Post by Elfy on 2015-02-24
If you really want to use v35 grab it from the utopic repos - install it 

I've done that and pinned it - really annoying issue in v36 with vivid - click a link to open in browser and it opens a new blank ff - at least that's what I've seen in hexchat

---

### Post by Ian_Worrall on 2015-02-25
I enabled vivid proposed & installed 36 - no issues so far.

---

### Post by Cavsfan on 2015-02-25
> **Ian_Worrall said:**
> I enabled vivid proposed & installed 36 - no issues so far.

Ditto. I like having the most up to date fox. I believe windows firefox updated to 36 yesterday. So why not?

---

### Post by Elfy on 2015-02-26
If generally people aren't having issues then perhaps it's just us xfce people then :)

[https://bugzilla.xfce.org/show_bug.cgi?id=11601](https://bugzilla.xfce.org/show_bug.cgi?id=11601)

Had to change the firefox.desktop file to 

X-XFCE-Commands=%B;
X-XFCE-CommandsWithParameter=%B "%s";

from the previous

X-XFCE-Commands=%B -remote "openURL(about:blank,new-window)";%B;
X-XFCE-CommandsWithParameter=%B -remote "openURL(%s)";%B "%s";

---

