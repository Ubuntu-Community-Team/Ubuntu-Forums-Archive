---
title: "Want a new graphics card for my Pangolin"
date: 2010-06-26
forum: System76 Support
---

### Post by bix15 on 2010-06-26
I have just recently been looking around for a new graphics card for my Pangolin laptop, since apparently my current one sucks. I say this because I tried to record my screen with gtk and the playback was all pixelated and choppy. Also when I went to play Alien Arena, or any graphic intensive game, it simply doesn't work. I think it is my graphics card since I already have 2GB of RAM....I mean that should be enough to be able to record my screen at the very least! 

Does anybody know what may be wrong? If it is my graphics card, I wouldn't know where to start in terms of finding a new one...I mean I wouldn't really know what to look for in terms of what would perform good enough for my needs ( being able to record my screen with gtk-record my desktop at the very least.)

Also I'm not sure what my current card is. I bought my laptop in November of 2009 and I believe they've completely changed the graphics card that is now being shipped with this computer.

Any help would be appreciated! 
Thank you!

---

### Post by bix15 on 2010-06-26
UPDATE!!

I do have a NVIDIA GeForce G 105M graphics card....

Details:   [http://www.notebookcheck.net/NVIDIA-GeForce-G-105M.13790.0.html](http://www.notebookcheck.net/NVIDIA-GeForce-G-105M.13790.0.html)

---

### Post by themrfreeze on 2010-06-27
You can't replace the video cards in laptops...they're an integral part of the motherboard (and in some cases part of the computer's main chipset).

---

### Post by betrunkenaffe on 2010-06-29
They switched from nVidia to ATI, ATI seem to be cheaper video cards and Linux support for them doesn't have stellar records.

---

### Post by cascade9 on 2010-06-29
> **themrfreeze said:**
> You can't replace the video cards in laptops...they're an integral part of the motherboard (and in some cases part of the computer's main chipset).

Sorry, wrong. If the laptop has the right port, then changing video cards is possible- 

[http://www.notebookcheck.net/Upgrade-Replace-a-Notebook-Video-Card.3236.0.html](http://www.notebookcheck.net/Upgrade-Replace-a-Notebook-Video-Card.3236.0.html)

As for if the Pangolin has a axiom/mxm slot, I dont know.

---

### Post by jbelmonte on 2010-06-29
> **cascade9 said:**
> Sorry, wrong. If the laptop has the right port, then changing video cards is possible- 

[http://www.notebookcheck.net/Upgrade-Replace-a-Notebook-Video-Card.3236.0.html](http://www.notebookcheck.net/Upgrade-Replace-a-Notebook-Video-Card.3236.0.html)

As for if the Pangolin has a axiom/mxm slot, I dont know.

The exception that proves the rule.

A reading of the article indicates that the chances of being able to replace the graphics on a laptop are remote at best. Even if the laptop has an MMX slot there is no guarantee it can be replaced.

> Some implementations of MXM will be field upgradeable, but many will not, depending on the platform implementation.

The Verdict of the linked article is:

> It is not easy to upgrade / replace the video card of a notebook. In case the notebook provides an upgrade possibility at all (in practice only, if the card is inserted in a MXM slot), buying the desired video card is an additional barrier. Sometimes, only looking at Ebay might help.

System76 can tell us if the Pangolin has an MMX slot and whether the graphics on the Pangolin is upgradeable, but I don't hold out much hope.

---

### Post by isantop on 2010-06-29
I need to know what model your pangolin is.

---

### Post by bix15 on 2010-06-29
It's a model panp6

---

### Post by isantop on 2010-06-30
Sorry, but the PanP6 is not upgradeable in terms of the graphics card.

It may be problem with your drivers. Go to System > Administration > Hardware Drivers and make sure the current version of the nvidia driver is enabled.

---

