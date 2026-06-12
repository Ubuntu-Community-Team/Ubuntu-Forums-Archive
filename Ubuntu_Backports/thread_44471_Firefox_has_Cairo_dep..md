---
title: "Firefox has Cairo dep.?"
date: 2005-06-26
forum: Ubuntu Backports
---

### Post by kamstrup on 2005-06-26
Is it me or does Firefox 1.0.4 depend on cairo >= 0.3.0... Well on my machine it does anyway... This makes it quite annoying that (the rather old) cairo 0.3.0 is the only available cairo package. I am coding some stuff that relies on the cairo 0.5.0 API and are about to get things mixed up.

I think what I'm saying/asking more or less is: How should I work aroud this, or are there newer cairo packages under way..?

Hint: If you're going to add cairo >= 0.5 please consider the pycairo package also. It's a great toy ;P

EDIT: BTW: Keep up the awesome work guys! :D

---

### Post by tim1 on 2005-06-26
Make sure you refreshed your apt database lately because should should have cairo 0.5.1 available, at least that's what I have her on breezy.

greets, tim

---

### Post by kamstrup on 2005-06-26
I'm not running Breezy, just using backports...

---

### Post by tim1 on 2005-06-26
Oh I'm sorry, I mixed up the subforums.

---

### Post by kamstrup on 2005-06-27
[QUOTE=tim1]Oh I'm sorry, I mixed up the subforums.[/QUOTE]
 Hehe... I also enjoy that sport occasionally :D

---

### Post by Slo Mo Snail on 2005-06-29
cairo 0.5.0 will not be backported as it is incompatible to 0.3.0 (which is in hoary) and both can't be installed side by side so there will be many problems...

---

