---
title: "Can I edit out buzzing?"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by metalf8801 on 2008-05-05
I have a recording of a concert and I want to edit out some buzzing I hear at different times. I was hoping someone could give me tips about how I can do that or at lest which program I could use.  

Thanks 
Dan

---

### Post by luctor on 2008-05-05
Audacity has a cool noise canceling filter.
first you sample a piece of the noice itself, then you can apply the filter
it's easy, you'll figure it out :-)

---

### Post by Stochastic on 2008-05-05
buzzing is a vague term, can you describe it a bit better?  is there always music going on when it buzzes or are there silent sections with the buzzing?  is the buzzing very loud, relative to the music?
you may want to check out gnome wave cleaner [http://gwc.sourceforge.net](http://gwc.sourceforge.net) as it has many specialized filters for noise analysis and removal.

---

### Post by metalf8801 on 2008-05-07
the buzzing is feed back from the PA system and its only happening when the band is playing but not if someone is just talking or when nothing is happening. 

I tried out the gnome wave cleaner and it didn't help.

---

### Post by Stochastic on 2008-05-07
Well then the next step is to precisely describe the sound so we can make an educated guess as to how to remove it.  Is it feedback as in a particular (high) pitch whining away?  Or is it buzzing, in a very quick knocking sort of way, as if the mic stand was vibrating rapidly against the floor/wall/etc...?  Or is it a lower pitched buzz that might come from a poorly grounded amp on stage?

Something to try would be to take a look at the sound through a spectrogram and see if any particular frequency is always there while the buzzing is going on (I think FreqTweak would be useful), then either use FreqTweak or a very precise eq to remove that frequency during those sections.

---

