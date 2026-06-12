---
title: "Nautilus and .sh files"
date: 2013-04-18
forum: Ubuntu Development Version
---

### Post by ELD on 2013-04-18
Okay so the old behaviour was that if i double click on an executable .sh file it would bring up a box asking if I wanted to edit, run or whatever but now it automatically just opens it in gedit which is really quite annoying.

Is there a way to get the old behaviour back?

---

### Post by ajgreeny on 2013-04-18
I suspect that the .sh files that just open in gedit are not marked as executable.  See what happens if you use command ```
chmod +x /path/to/file.sh
```and then double click it again.

I suppose this may possibly be a feature and not a bug in nautilus for RR, but it seems unlikely that would be so, though I am prepared to be shot down by someone telling me that is the case.

---

### Post by mc4man on 2013-04-18
The default behavior has been changed, set as desired in nautilus preferences

---

### Post by ELD on 2013-04-18
> **ELD said:**
> Okay so the old behaviour was that if i double click on an** executable .sh file** it would bring up a box asking if I wanted to edit, run or whatever but now it automatically just opens it in gedit which is really quite annoying.

Is there a way to get the old behaviour back?

I stated this.

> **mc4man said:**
> The default behavior has been changed, set as desired in nautilus preferences

Interesting, an annoying change.

---

### Post by azangru on 2013-04-28
> **mc4man said:**
> The default behavior has been changed, set as desired in nautilus preferences

Thank you, I had exactly the same problem! I've never even looked in Nautilus preferences! Glad it can be solved so easily.

---

### Post by QDR06VV9 on 2013-04-28
> **mc4man said:**
> The default behavior has been changed, set as desired in nautilus preferences

Thanks!
Ive been meaning to do a search for this soon.
Saved me some time:popcorn:

---

