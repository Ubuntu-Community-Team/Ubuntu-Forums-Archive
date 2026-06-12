---
title: "Chromium browser finds Flash in &quot;.mozilla&quot;"
date: 2010-06-04
forum: The Cafe
---

### Post by kelvin.illa on 2010-06-04
I installed Ubuntu on new machine and was dumbfounded by the notion that I had to again install flash on my 64bit Chromium browser. This was because Chromium didn't need Flash when I installed in my other machine; I thought Flash was built-in with Chromium. It turns out Chromium was using the Flash plugin (libflashplayer.so) from my /home/<username>/.mozilla/plugins folder. I took the folder away to test if this was true, and the Flash on Chromium stopped working.

That's amazing! Has anyone else noticed this? I think if anyone should make a tutorial for installing 64bit Flash on Chromium, this is another way of doing it--having Flash on both Firefox and Chromium.

---

### Post by RiceMonster on 2010-06-04
You can also put it in /usr/lib64/mozilla/plugins/ if you want it to be system wide, rather for your account only.

---

### Post by zekopeko on 2010-06-04
> **kelvin.illa said:**
> I thought Flash was built-in with Chromium.

Flash comes with Google Chrome not Chromium.

---

### Post by kelvin.illa on 2010-06-04
> **RiceMonster said:**
> You can also put it in /usr/lib64/mozilla/plugins/ if you want it to be system wide, rather for your account only.

Nice... I'll do that.

---

