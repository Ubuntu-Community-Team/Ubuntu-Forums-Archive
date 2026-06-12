---
title: "looking for a good document formatting utility"
date: 2008-09-01
forum: Ubuntu Studio
---

### Post by teryret on 2008-09-01
Hello all.  I'm in the process of job hunting, and for that I need a nicely laid out resume.  The critique I got from my college's career center was to lay it out differently, in a way that I can't achieve with OOo (or M$ Office either).  

My friend told me about LyX, which seems to be exactly the opposite of what I need; all content and no layout.  I'm looking for the most powerfull text layout and formatting tool I can get.  If I can't figure this out soon I'm just going to use GIMP (which would take a long time), so any ideas for formatting software would be most appreciated, thanks!

---

### Post by eric71 on 2008-09-01
Scribus sounds like what you need.

---

### Post by teryret on 2008-09-01
That was exactly what I needed, thanks!

Edit:  I'd like to hear other people's ideas too, since after an hour of playing with scribus I've encountered some bugs that have rendered it nigh-useless to me.

Edit2:   After another hour of playing with it I've managed to work around the issue.  It turns out the bug I was facing only happens when the user is stupid and screws up a tab stop placement.

I had two tabs closer together than some of the words that would have to fall between them.  Normally this would cause them to be off by one tab, but since one of the the tabs was right justified, the two "free ends" that would fall between the tabs overlapped, which would then synchronize down to the document (from the story editor) with characters missing.  Then when that synchronized back up to the story editor the formatting was worse than it had been (including missing tabs and missing characters), and the feedback loop got worse each time I replaced the damaged text with the right text.

Ultimately I got it all working by simply putting my tab stops in the right places and retyping the corrupted parts of the text, but that feedback loop is definately a bug, content should never be lost unless I manually delete it.

---

### Post by Stochastic on 2008-09-01
my opinion on this one: use scribus.

also: FILE YOUR BUGS!!!   FILE YOUR BUGS!!!
[**http://ubuntu.launchpad.net**](**http://ubuntu.launchpad.net**)
-create an account
-explain any bugs to the developers
-help the project advance!
:)

You might also be interested in the ubuntustudio-graphics metapackage, it contains a number of useful tools for graphical/publishing work.

---

