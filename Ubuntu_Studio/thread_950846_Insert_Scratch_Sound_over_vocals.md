---
title: "Insert Scratch Sound over vocals"
date: 2008-10-17
forum: Ubuntu Studio
---

### Post by secondstage on 2008-10-17
Is there a plugin, or program that will allow me to select just a section of a track, and then use a DJ scratch effect to cover up some explicit words?

---

### Post by unutbu on 2008-10-17
I've never used this myself, but it seems to fit the bill: [http://terminatorx.org/](http://terminatorx.org/)

It's even in the official repo:
```

sudo apt-get install terminatorx
```

---

### Post by secondstage on 2008-10-17
You can't select a part and then scratch, you have to scratch the whole thing or nothing. Great program though.

---

### Post by Stochastic on 2008-10-18
you'll need to record the output of terminatorx by connecting it's output in qjackctl to any wave editor/recorder (audacity, ardour, rezound, etc...)  then copy, mix-paste it into the section of audio you're wanting to use.

The other way, which I've used to 'clean' tracks with, is to just select the word in your favorite wave editor, and reverse that section.  It covers up most words just fine, but some seem to still creep through, so additional samples of say a kick drum or dj scratch can also be added where needed.

---

### Post by secondstage on 2008-10-20
Thats works great. S*** is still understandable when reversed, but after phasers, wah-wahs, and a scratch, it sounds like it would be just a part of the song.

---

