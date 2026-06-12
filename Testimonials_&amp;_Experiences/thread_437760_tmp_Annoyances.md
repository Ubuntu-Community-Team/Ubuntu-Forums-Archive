---
title: "/tmp Annoyances"
date: 2007-05-09
forum: Testimonials &amp; Experiences
---

### Post by Blofeld on 2007-05-09
A word to the wise:  the /tmp directory should not be used for temporary storage.  Especially not for holding two months' worth of miscellaneous writings while the system reboots.
In fact, /tmp should not be used for storage at all, NEVER EVER, and would in fact be more appropriately named /del.

---

### Post by Stephen Howard on 2007-05-09
That's not an annoyance, its actually doing the right thing.  The Unix Filesystem Hierarchy reserves /tmp as a directory that is erased every reboot - indeed lots of people (me) use a ram based /tmp directory.  If you want something that lasts through multiple boots but isn't guaranteed permanent (say a multi-day dhcp lease), then use /var/tmp.

Um, never store any user-wanted files in either /tmp or /var/tmp, that'd be asking for upset users...

---

### Post by Blofeld on 2007-05-09
... or admins (sobs) ...

---

### Post by Jonne on 2007-05-09
Lol, I can't help but laugh at this. Nothing personal, Blofeld. At least you didn't store your stuff in  /dev/null ;) .

---

### Post by weblordpepe on 2007-05-09
Everyone's old lost socks, lost keys, unsaved C code after a reboot, and long lost teddybears throughout the world are all lost into the void that is /dev/null

---

### Post by Blofeld on 2007-05-09
Actually I was aware that /dev/null is ... well, /dev/null.  I literally wanted to store some data temporarily over a reboot, was a bit in a fug, and /tmp sounded like a good enough directory.
What's more, I regularly backed up for the past couple of years at least once a week, and then let up a few weeks ago.
Oh well, you live and learn.

---

