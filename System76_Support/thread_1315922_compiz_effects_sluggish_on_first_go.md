---
title: "compiz effects sluggish on first go"
date: 2009-11-05
forum: System76 Support
---

### Post by felixnine on 2009-11-05
pangolin, karmic up-to-date, nvidia g105m.

after i've been on one workspace for a while (i figure about a minute or so, maybe less), i notice that if i scale all windows or switch the workspace (using desktop wall), the animation is really sluggish and choppy the first time. the second time, if its within that minute or so, it's super smooth like normal. anyone else?

---

### Post by kyuubi777 on 2009-11-05
not the case for me... it's always smooth on my machine (and it's got crappy intel integrated graph card)

---

### Post by HotShotDJ on 2009-11-05
> **felixnine said:**
> i notice that if i scale all windows or switch the workspace (using desktop wall), the animation is really sluggish and choppy the first time. the second time, if its within that minute or so, it's super smooth like normal. anyone else?This is due to the adaptive GPU scaling feature in NVidia mobile graphics adapters.  It is not a bug. I talked about this in more detail [HERE]("http://ubuntuforums.org/showthread.php?t=1311946").

---

### Post by HotShotDJ on 2009-11-05
> **kyuubi777 said:**
> not the case for me... it's always smooth on my machine (and it's got crappy intel integrated graph card)Correct.  Intel integrated graphics adapters do not have adaptive scaling... they don't need it. ;)

---

### Post by felixnine on 2009-11-05
ahhh, had no idea. thanks!

---

