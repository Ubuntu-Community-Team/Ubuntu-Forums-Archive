---
title: "Memory leak in Compiz &amp; Unity-Scope-Home"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by speartip on 2014-03-28
Been testing 14.04 now for about 6 weeks, & the issue of High memory, particularly in Compiz still remains.
I have attached a screenshot of my system monitor.
In 12.04 memory used by compiz was between 40-100mb.
Is anyone else having the same problem?
[ATTACH=CONFIG]251527[/ATTACH]

---

### Post by Mateusz Stachowski on 2014-03-28
I had problems in 13.10 with clementine scope triggering memory leak but no more in Trusty. 

Check that python3 process which is one of scopes and then when you now which one is it disable it from Application lens > Filter results > Dash plugins.

---

### Post by mc4man on 2014-03-28
Don't see anything near that here, particulary the home scope which is usually around 10Mb
At log in compiz is around 40Mb, basic use of the Dash, ect.  may up to 80 - 90 over time & use.

There is one thing that does do a large increase but it's a one time increase - that's the applications lens > Installed >   see xx more results
Using that causes  an immediate 100Mb+ increase but repeated use doesn't increase usage (100+ does seem a lot to display 100 icons or so...

---

### Post by speartip on 2014-03-28
Thanks for your replies guys.
Mateusz..  I think you may have hit on the issue, as you can see from my 2 screenshots now.
The 1st one is after a normal logging & opening the dash - Memory is mega high.
The 2nd screenshot is after I uninstalled "unity-scope-clementine", memory now more or less normal.
Will post back if things change.
Thanks again.[ATTACH=CONFIG]251546[/ATTACH][ATTACH=CONFIG]251547[/ATTACH]

---

### Post by speartip on 2014-04-02
Just to add a bit more info to this post. Uninstalling unity-scope-clementine helped massively, but even so, Compiz still crept up from 40mb to about 250mb.
So I reset unity/compiz back to factory settings, as I had tweaked it & enabled wobbly windows. This seems to have resolved the problem. 3 hours uptime & compiz is using only 79mb. So it seems unity needs leaving alone after installation to stop this happening.

---

### Post by darkhole on 2014-05-08
I have the same problem, I' on Ubuntu 14.04 with an nVidia Optimus video card. In home, on my Dell Vostro 3450 I don't have any issue.
I'm using the nVidia propietary driver, how is your setup?

---

### Post by Elfy on 2014-05-08
IF you have an issue with 14.04 and compiz you need to start a thread - I would suggest here [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

We're not working with 14.04 anymore - 14.10 is the topic in here now.

Closing this old discussion.

---

