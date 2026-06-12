---
title: "Massive update today?"
date: 2008-10-17
forum: The Cafe
---

### Post by Watchtow3r on 2008-10-17
What's up with the massive update today? Usually updates are just a few kb's, this one for me is about 85 mb. I know the new Ubuntu is almost out, does that have anything to do with the big update? Also I know it's partly my own programs that I have installed, but most are just generic Ubuntu files. So what's up with the giant update? (not that that's a bad thing, anything to help ubuntu run better is ok with me!)

---

### Post by snova on 2008-10-17
I noticed earlier today there was about 160 MB of KDE updates that appeared overnight. I don't even use backports, so this was strange.

---

### Post by Calmatory on 2008-10-17
Guess someone pushed the Red Button a good few times. :)

---

### Post by snova on 2008-10-17
Poking through the kdelibs debian changelog, there was nothing more than:

```

kdelibs (4:3.5.10-0ubuntu1~hardy1) hardy-backports; urgency=low

  * Upstream bug fix release (LP: #261366)
    - Dropped kubuntu_98_kate_paste_cursor.diff applied upstream
    - Dropped kubuntu_9903_kinit_integer_overflow.diff applied upstream

 -- Scott Kitterman <scott@kitterman.com>  Mon, 25 Aug 2008 23:37:18 -0400

```

I haven't noticed any difference except that Kicker looks a little funny now (transparency issue).

---

