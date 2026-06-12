---
title: "Starling sleep/standby/suspend oddity[1]: if idle sleep, no login on wake"
date: 2010-01-11
forum: System76 Support
---

### Post by tlroche on 2010-01-11
I'm using a nearly-new Starling (model=star1, ubuntu=UNR 9.04), not much customized except that I used gconf-editor to make it show the screenlock GINA (i.e. the screenlocker login "window" with the buttons) on resume: see [this post]("http://ubuntuforums.org/showpost.php?p=8571646&postcount=3") for details. This works, except in one case: if I leave the Starling running until its idle timeout is reached, and it sleeps. If I then hit the power button to wake it, it goes right back to the previous session, with no GINA. How can I make it behave properly (or, at least consistently) in this case? i.e. to force login on wake after sleep after idle timeout?

---

