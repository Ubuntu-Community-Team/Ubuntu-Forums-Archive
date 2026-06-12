---
title: "tuning a tin whistle: pitch generator needed"
date: 2012-04-25
forum: Ubuntu Studio
---

### Post by john.errington on 2012-04-25
I play tin whistles. The best way I have found to tune these is by comparison with a fixed tone of the correct frequency. (using audacity generate.)
Now I need to be able to play correctly pitched notes in quick succession - so I'm looking for a software sinewave generator - a bit like a virtual piano, organ or synth.
And command line is no good, I need to be able to change quickly from any one to any other.
I've searched the web but keep getting programs for a PC under windows (yuk).
Hope someone can help.

---

### Post by jejeman on 2012-04-25
Any softsynth can do that, e.g. ZynAddSubbFx.

---

### Post by john.errington on 2012-04-25
Thanks for quick reply.
it looks wildly complicated.  I'm an ubuntu newbie.
what i need is a simple press a key - get a tone
like a virtual organ etc. I dont have a midi keyboard.
I've installed yoshimi but when i click the icon to start it it does the turning circle icon, the nothing.

Silly me yes I ran Qjackctl and now yoshimi is working fine, and I can record to audacity.  However I still cant get it to sound because Jack is showing no output devices!

---

### Post by jejeman on 2012-04-25
For Yoshimi you need jack server, ZynaddsubFx works with just alsa. Thats why I recommended it, also it has built in virtual keyboard.

If you want to use Yoshimi you need to install and setup jack server.

---

