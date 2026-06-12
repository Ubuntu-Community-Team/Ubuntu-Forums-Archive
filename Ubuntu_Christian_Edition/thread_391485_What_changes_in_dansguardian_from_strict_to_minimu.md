---
title: "What changes in dansguardian from strict to minimum filtering ?"
date: 2007-03-23
forum: Ubuntu Christian Edition
---

### Post by glenn69 on 2007-03-23
I am running ubuntu ce v2.2.

I have been having trouble downloading podcasts.  If I stop firehol, the podcasts will download.  If I leave firehol running the podcasts will not load.  I am not having much success figuring out exactly why this is.

Dansguardian now has an enhanced gui in ce v2.2.  If I change filtering to minimum, instead of the default of strict, then my podcasts will download with no other changes having been made to firehol.

What changes are made when I press minimum filtering as opposed to strict?  I checked dansguardian.conf, but there were no changes made there.

Thanks

---

### Post by mysticrider92 on 2007-03-23
You should probably check 'Blocked File Extentions' and 'Blocked Mime Types' in the Advanced tab of the GUI. Put a # in front of any line that blocks media (you may also want to not block archive types and similar things). I am not sure exeactly what the difference in the Strict/Minimum filtering is, mhancoc could answer that.

---

### Post by mhancoc7 on 2007-03-23
You can click the "?" button next to each filter setting to see what the differences are.
Jereme

---

