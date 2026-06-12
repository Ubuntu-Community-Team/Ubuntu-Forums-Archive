---
title: "Eclipse editor and console fonts  changed after upgrade"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by renataogarcia on 2012-03-26
I've upgraded from oneiric to precise and the font on Eclipse editor and console seem to have shrunk a little? I've checked the definitions on Eclipse and they are the same. Not sure if this has happened for the whole system, but I can notice it on the editors and console because they definitely are not looking good as it used to be.

Any idea why this might have happened and what can I do fix it? (If I increase it from 10 to 11 it becomes just too big).

It happens Gnome Shell and Unity.

---

### Post by effenberg0x0 on 2012-03-26
> **renataogarcia said:**
> I've upgraded from oneiric to precise and the font on Eclipse editor and console seem to have shrink a little? I've checked the definitions on Eclipse and they are the same. Not sure if this has happened for the whole system, but I can notice it on the editors and console because they definitely are not looking good as it used to be.

Any idea why this might have happened and what can I do fix it? (If I increase it from 10 to 11 it becomes just too big).

It happens Gnome Shell and Unity.

Now we have MyUnity in the repos. You can install it with sudo apt-get install myunity

Check in MyUnity, in the fonts tab, your settings for "documents" fonts. I believe desktop fonts are larger too.

Regards,
Effenberg

---

### Post by renataogarcia on 2012-03-26
Effenberg, it seem to be fixed now after updating today. I had the latest updates yesterday. I believe it was an issue with anti-aliasing.

Thanks

---

