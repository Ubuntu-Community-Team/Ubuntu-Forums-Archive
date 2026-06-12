---
title: "Newbie with a Ardour3/Jack Question"
date: 2014-08-12
forum: Ubuntu Studio
---

### Post by matthew49 on 2014-08-12
Hey Guys. So i decided to give Ubuntu Studio a whirl and i am really enjoying it so far. The one issue I'm having is with Ardour. It does everything I want it to very well but once i exit and go in to other applications, Youtube for example, the sound won't work unless i manually go in to Task manager and stop Jack. Is there something I'm missing here? Please be easy on me. I'm new to Linux after finally dumping XP a couple of days ago. Thanks for the help!

---

### Post by jejeman on 2014-08-13
Yep, you need to close JACK.
See if there is maybe a close script in Ardour, so you can pass a kill command for JACK. Or don't start JACK with Ardour, but with Qjackctl, so it will remind you that you need to turn off JACK (by closing it).

---

