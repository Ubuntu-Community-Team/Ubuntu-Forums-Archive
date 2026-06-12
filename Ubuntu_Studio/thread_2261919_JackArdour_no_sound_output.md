---
title: "Jack/Ardour no sound output"
date: 2015-01-21
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2015-01-21
Ardour 3.5.380
Jack 3.1.1
Ubuntu Studio 14.10

Usually, at least for me, if I'm on Firefox or elsewhere and audio is being output, if I start anything jack related, jack takes over all audio and nothing else works, but jack works perfectly. 
This time, I want to record something in Ardour, but jack isn't outputting any audio. The audio in Firefox works with jack running for some reason. 

Any ideas?

---

### Post by ATMarsden on 2015-01-22
This happens to me, occasionally, too.

The last time this happened, however, was yesterday - recording through JACK into Audacity worked fine for me, but it wouldn't play back. When I switched back to ALSA (and closed JACK), my computer started crashing around me, and now I can't log in.

The fact that someone else is presenting a similar JACK problem makes me think that it's related, even if your results weren't as catastrophic as mine. (My problem is in a [separate thread]("http://ubuntuforums.org/showthread.php?t=2261839")).

---

### Post by Tristan_Williams on 2015-01-22
> **ATMarsden said:**
> This happens to me, occasionally, too.

The last time this happened, however, was yesterday - recording through JACK into Audacity worked fine for me, but it wouldn't play back. When I switched back to ALSA (and closed JACK), my computer started crashing around me, and now I can't log in.

The fact that someone else is presenting a similar JACK problem makes me think that it's related, even if your results weren't as catastrophic as mine. (My problem is in a [separate thread]("http://ubuntuforums.org/showthread.php?t=2261839")).

It works perfectly recording into Audacity, but I really can't be productive with audacity like I can with Ardour

---

