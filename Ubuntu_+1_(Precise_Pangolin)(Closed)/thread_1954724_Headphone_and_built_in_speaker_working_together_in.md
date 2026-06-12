---
title: "Headphone and built in speaker working together in Ubuntu 12.04"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kaziweb on 2012-04-08
If I connect my head phone to my laptop it doesn't stop my laptop built in front speaker. Headphone works properly but at the same time laptop speakers also plays.

It supposed to stop as soon as I connect my headphone to my laptop which is not happening and when I remove my headphone from my laptop the sound should immediately go to my laptop front speaker.

If I connect my headphone to my laptop and restart it my headphone works. But If I remove my headphone the sound is not going to built in front speaker automatically.

I've reported a Bug ---> [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/995684](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/995684)

I'm looking for a solution. I'm not getting any solution on this posting this problem to other sites. Thanks.

---

### Post by na5h on 2012-04-08
If you use alsamixer, you could just mute the front speaker so that it doesn't bother you while using headphones. Just open a terminal and type "alsamixer". Then use the arrow keys to change the volume of the different channels (headphones, front speaker, master volume, etc.).

Alas, this is no permanent solution to your problem.
Perhaps someone else has a more permanent solution?

---

### Post by williammanda on 2012-04-08
I have noticed a similar problem using skype and mythtv (or a streaming video over the internet). Both programs play at the same time on either the computer speakers or the headset. Using prior versions of ubuntu, skype would just play on the headset while mythtv would play on the computer speakers. Interest note...skype is using pulse audio while mythtv uses alsa.

---

