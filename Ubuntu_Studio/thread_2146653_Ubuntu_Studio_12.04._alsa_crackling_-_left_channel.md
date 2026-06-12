---
title: "Ubuntu Studio 12.04. alsa crackling - left channel, audiophile 2496"
date: 2013-05-19
forum: Ubuntu Studio
---

### Post by bishaljux on 2013-05-19
I've used Ubuntu Studio 8.04 and 10.04  with this soundcard and everything worked fine. Now, with new machine and Ubuntu Studio 12.04, left analog out channel is crackling(produces bad CD-like sound)  if using ALSA driver. While using JACK, everything works fine. I tried and reinstalled all alsa packages i could find in synaptic - no change. Tried messing around with card setings in mudita mixer and pulseaudio gui - no luck.Tried this, tried that, tried all i could think of,  but the problem persisted...
So, here we have a Ubuntu Studio 12.04 LTS+M-Audio Audiophile 24/96+ALSA driver( +Pulseaudio server?) problem.
alsa info:
[http://www.alsa-project.org/db/?f=a5033f704d25109b5b3bd584e3c460839d3b3d8d](http://www.alsa-project.org/db/?f=a5033f704d25109b5b3bd584e3c460839d3b3d8d)

---

### Post by jejeman on 2013-05-19
You can not use JACK without ALSA (for that card). So it is not ALSA problem, but more likely pulseaudio.

---

### Post by bishaljux on 2013-05-19
Yeah, that's a good point. Hell, it didn't even cross my mind:) . So, removing pulseaudio could be the solution?
Should i expect problems with Mplayer, Flash plugin etc?

---

### Post by jejeman on 2013-05-19
No problems with Mplayer and flash without pulseaudio.
You don't need to remove it, just turn it off.
```
echo "autospawn = no" > ~/.pulse/client.conf
pulseaudio -k
```

---

### Post by bishaljux on 2013-05-19
Thanks, but i ended doing something else...
I have been impatient and tried to remove pulseaudio using various  commands...probably messed it up a little but didn't remove it  completely , then tried your code to shut it off - didn't work(that's  understandable:) ). Then I installed standard desktop Ubuntu 12.04, but  the problem was still there...Tried to fix with your code and various  other advices i found here and there - didn't work.  Aldo it didn't have  the stuff i need, i hated the fact i have to leave that disto behind  cause i realy liked that Unity DE. It's pretty and functional... So, in  the end, i grabbed AV Linux CD i had at my desk and installed it.  Everything works like a charm right out of the box, and all the stuff I  need is there. My problem's solved, but not the way i  hoped.
Funny  thing is, I instaled Ubuntu Studio 12.04 to my brother's old crap laptop  and it worked, and still works, but it doesen't wanna work with the  hardware that it's supposed to work with...Too bad, cause i really think  Ubuntu Studio's a killer distro., and i'm so used to it. I hope this  problem will go away in the near future.

---

