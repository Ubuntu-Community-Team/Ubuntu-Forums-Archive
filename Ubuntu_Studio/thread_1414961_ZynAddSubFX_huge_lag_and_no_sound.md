---
title: "ZynAddSubFX huge lag and no sound"
date: 2010-02-24
forum: Ubuntu Studio
---

### Post by dwebb86 on 2010-02-24
I got ZynAddSubFX when I had 9.04, now I have 9.10. It worked properly before. I'm not sure if it had to to with the version upgrade or some other upgrades, or something else altogether, but when I open it now it lags when opening, has HUGE menu and button lag, and doesn't produce sound when I hit keys. 

I've looked all over for a solution for about two days now, the closest thing I can find is [http://bugs.archlinux.org/task/18132?project=5](http://bugs.archlinux.org/task/18132?project=5) but I have no clue how to even implement this to see if it works for me. Might not even apply to me or work as a solution.

Anyone else have this problem or can help me solve it? If you need more info, let me know what to do to get it for you. Thanks for any help.

---

### Post by cchhrriiss121212 on 2010-02-24
Are you using jack or alsa? I had poor performance with zyn and jack until I increased the timeout setting to a higher value.

---

### Post by dwebb86 on 2010-02-24
Well, I'm not completely sure. I have JACK Control, but I've seen alsa all over the place too. I really don't know what I'm talking about when it comes to the differences. 

Something I can check to tell you?
How did you change the timeout setting?

Also, "poor performance" is an understatement when considering my problem. The program just doesn't work. I click a menu and it takes 5-10 seconds to pop up, I click and hold a key and it takes that long to register and makes no sound.

---

### Post by cchhrriiss121212 on 2010-02-24
Well jack and alsa work together, what I meant was whether you start up jack by going to applications>sound>jack control, pressing the start button, then opening zyn.

If jack starts up OK, then open the setup window and increase the timeout setting near the bottom to anything over 1000.

It sounds like you may be having a different problem than I had, but try it out anyway.

---

