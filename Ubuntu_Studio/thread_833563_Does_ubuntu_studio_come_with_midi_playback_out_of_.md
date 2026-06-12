---
title: "Does ubuntu studio come with midi playback out of the box?"
date: 2008-06-18
forum: Ubuntu Studio
---

### Post by shtewe on 2008-06-18
at the moment, i am using ubuntu 8.04 and it is very annoying because i need MIDI playback and i have tried to install all those packages and none work.  

I really need it for tuxguitar since i am a bassist and want to learn some songs.  Please help.

I am downloading ubuntu studio and just wondering if it comes with midi playback out of the box support.

:guitar:

---

### Post by Stochastic on 2008-06-18
Provided you do ```
sudo apt-get install ubuntustudio-audio
``` midi should work for you (but you'll also get a bunch of other applications you may not need, along with a new realtime kernel).

TuxGuitar actually uses its own midi playback system from the Java Sound API (according to this post: [http://www.tuxguitar.com.ar/forum_posts.html?fid=4&tid=33&view=NEW](http://www.tuxguitar.com.ar/forum_posts.html?fid=4&tid=33&view=NEW)) so if you're having troubles with it, I don't think ubuntustudio will actually help much, although that thread is a little over a year old.  You should start to troubleshoot your TuxGuitar app rather than trying to get general midi working.

---

### Post by shtewe on 2008-06-18
cool, i am installing ubuntu studio now.

i will let you know how things go

---

### Post by atomkarinca on 2008-06-18
> **shtewe said:**
> cool, i am installing ubuntu studio now.

i will let you know how things go

For TuxGuitar you should install Timidity. I can't remember whether Ubuntu Studio meta packages include that or not so if it doesn't install, this is what you should do: open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo apt-get install timidity
```

then open up TuxGuitar and Tools > Settings > Sound tab, change MIDI port to one of the Timidity ones. This way you'll have a much better sound.

---

