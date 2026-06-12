---
title: "Alarm clock script"
date: 2008-04-24
forum: The Cafe
---

### Post by cartisdm on 2008-04-24
My programming experience is limited to what I've learned in a semester of VB at college so I am shooting in the dark here.  I really like to listen to a morning radio show that I have to stream online (I don't live in the broadcasting area anymore).

What would it take to write a script (forgive me if I use the wrong terminology) that would load their streaming page in a browser at a designated time like an alarm clock.  I could just leave my volume up then have it wake me up in the morning:)

I'm open to learning a new language (such as python) if possible - this could be my practice project.

---

### Post by Stenico on 2008-04-24
That should be incredibly easy. There are simple ways of running a command at the time of your chosing.

You should investigate the cron daemon e.g. [http://www.linuxhelp.net/guides/cron/](http://www.linuxhelp.net/guides/cron/) which allows you to schedule repeat tasks and the 'at' command e.g. [http://linux.about.com/library/cmd/blcmdl1_at.htm](http://linux.about.com/library/cmd/blcmdl1_at.htm) which allows you to run a command at the time of your choosing.

You can then just schedule your browser to open at the correct page at whichever time you choose and it should just work. e.g. to open firefox at the bbc website I would just type "firefox www.bbc.com".

What would be harder problem for you to solve is to make your computer resume from hibernation at the right time before launching the browser. I have a script somewhere at home that did this to wake my computer and then play the TV news in the mornings.. I would really love to see a nice gui alarm clock app for gnome that gracefully handled all the suspend/resume stuff.

---

### Post by cartisdm on 2008-04-24
Thanks man! Soon as I get home from work I'll look into that some more

---

### Post by cartisdm on 2008-04-24
duuuuuuuuuuuuuude.  KAlarm.  I found it in the Add/Remove programs.  Works like a charm and makes life easy for my non-programming self;)

---

