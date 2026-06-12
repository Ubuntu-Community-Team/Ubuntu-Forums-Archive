---
title: "Rosegarden does not play instruments on alternate banks"
date: 2008-10-11
forum: Ubuntu Studio
---

### Post by Jeek on 2008-10-11
I have been trying Rosegarden for a while (running on Timidity only as JACK does not work) and it mostly works, except for one thing.

I am using the Ultimate.SF2 soundfont, which has a number of instruments on different banks (0:0, 0:1, etc.).  However, so far I can only play the instruments on the main bank (0:0), and when I try to pick one from another bank, the instrument is automatically changed to its equivalent on 0:0.

I have tried playing with the event editor as mentioned on [this page]("http://wiki.debian.org/DebianEdu/Documentation/Manuals/Rosegarden/AllInOne#head-50013b99da0debc353e9a2b4839954a8006b0925"), but it does not work.

Now what can I do?

---

### Post by alloftheabove on 2008-10-16
Honestly, I'm just now getting into looking at soundfonts and how to use them.  I would recommend sending a bug report, or just contacting the people that make rosegarden.  By the way, are you using the version compiled from source, or apt-get install?

---

### Post by Jeek on 2008-10-25
Sorry for the bump, but I just realized the problem is not about changing banks.  Rather, it is an inability to use any sound other than the default ones from Rosegarden.

I installed Rosegarden through apt-get, and set up the soundfont using the [tutorial]("http://www.rosegardenmusic.com/wiki/setting_up_the_fluidr3_gm.sf2_for_timidity") shown on the Rosegarden website. I can listen to MIDI files as well, if that information is of any help.

---

