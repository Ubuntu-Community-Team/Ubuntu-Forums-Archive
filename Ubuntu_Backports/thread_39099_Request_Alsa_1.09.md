---
title: "Request: Alsa 1.09"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by stoffe on 2005-06-03
Hello, I would like to request that ALSA 1.09 would be backported. The reason for this is that Beep Media Player won't work to its fullest for me without it: when using earlier ALSA versions, it just freezes all the time, and I haven't gotten the other backends (eSound, OSS) to play nice with other sound sources. I'd really appreciate this, so I can enjoy a good GTK2 player. :)

The bug entry for this issue, with a statement that it will work from 1.09 (and what is needed) at the bottom: [http://www.sosdg.org/~larne/bugs/show_bug.cgi?id=115](http://www.sosdg.org/~larne/bugs/show_bug.cgi?id=115)

ALSA: [http://www.alsa-project.org/](http://www.alsa-project.org/)

Anything else that I could/should provide, just ask. :)

---

### Post by Technoviking on 2005-06-03
[QUOTE=stoffe]Hello, I would like to request that ALSA 1.09 would be backported. The reason for this is that Beep Media Player won't work to its fullest for me without it: when using earlier ALSA versions, it just freezes all the time, and I haven't gotten the other backends (eSound, OSS) to play nice with other sound sources. I'd really appreciate this, so I can enjoy a good GTK2 player. :)

The bug entry for this issue, with a statement that it will work from 1.09 (and what is needed) at the bottom: [http://www.sosdg.org/~larne/bugs/show_bug.cgi?id=115](http://www.sosdg.org/~larne/bugs/show_bug.cgi?id=115)

ALSA: [http://www.alsa-project.org/](http://www.alsa-project.org/)

Anything else that I could/should provide, just ask. :)[/QUOTE]
I will look at backporting, but I use bmp with alsa all the time. 

Try this:
Goto Preferences > Output > Click on Preference Button > Advanced Settongs Tab > uncheck MMAP mode.

Mike

---

### Post by Technoviking on 2005-06-03
Alsa 1.0.9 is not in breezy yet, will check again in a couple of days.

Mike

---

### Post by stoffe on 2005-06-03
[QUOTE=Mike Basinger]I will look at backporting, but I use bmp with alsa all the time. 

Try this:
Goto Preferences > Output > Click on Preference Button > Advanced Settongs Tab > uncheck MMAP mode.

Mike[/QUOTE]

Thanks, that seems to have done the trick! I've really been searching for this issue, but I didn't find that one, just the ALSA bug. Out of curiosity, what does MMAP do?

---

### Post by Technoviking on 2005-06-03
[QUOTE=stoffe]Thanks, that seems to have done the trick! I've really been searching for this issue, but I didn't find that one, just the ALSA bug. Out of curiosity, what does MMAP do?[/QUOTE]

[http://old.lwn.net/lwn/1998/0326/sounddriver.html](http://old.lwn.net/lwn/1998/0326/sounddriver.html)

---

### Post by RiotRick on 2005-06-23
Ok. I will try switching mmap off too. I was having the same problems here. Hope this will fix it for now. A backport of alsa 1.0.9 would be nice though.

---

