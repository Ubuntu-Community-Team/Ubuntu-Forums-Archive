---
title: "Ivy bridge HD 4000 video refresh settings, 50 Hz (EU), 60 Hz (VS), etc"
date: 2013-03-02
forum: Ubuntu Development Version
---

### Post by jchuit on 2013-03-02
I have installed Ubuntu 13.04, but I am facing a problem with the European video settings.
The HD-video (25/50 Hz interlaced) are played back at 60 Hz, giving a non-stable (fluid) video playback, a 10 Hz refresh out of sync.

There are country settings in Ubuntu, shouldn't these be handling the video refresh rate?

Now, I use an Intel 3225 @ shuttle xh61v with the Ivy bridge HD 4000 video refresh settings of 60 Hz (VS), 
I like to change this to 50 Hz, 75 Hz or 100 Hz (a multiple of 25 Hz).

Does anybody has an idea how to change this? 

For the programmers: Can a configuration setting be integrated in 'about this computer'? And can the refresh rate default to the correct region settings?

---

### Post by dino99 on 2013-03-02
the kernel set the highest rate possible, depending on the screen size and the encoded video. Of course its always the most limited element that set the final choice.

note: devs quite never spend their time here on forum. If you think you have met a bug, or like to request a feature, then post a bug report on launchpad:

```
ubuntu-bug thepackagename2blame
```

---

