---
title: "Busted window (manager)?"
date: 2012-04-10
forum: Ubuntu Studio
---

### Post by lemonbar on 2012-04-10
I'm running 12.04, and I love it so much - the transition to x was a little rough because I started with the previous release, but even early in the Beta stage 12.04 was fantastic - great job!  My only issue is that saving sessions breaks the window manager.  Looking through the forums I found [this]("http://ubuntuforums.org/showthread.php?p=11833708&posted=1#post11833708"), which made me happy. Running
> xfwm4 --daemon
works to fix it, and removing the saved sessions:
> rm -r ~/.cache/sessions
made it stop happening every time, but I'd like to use the saved sessions function in the future - how do I do that without screwing everything up again?


Thanks!
Laurie

---

