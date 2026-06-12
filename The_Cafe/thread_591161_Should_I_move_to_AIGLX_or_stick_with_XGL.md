---
title: "Should I move to AIGLX or stick with XGL?"
date: 2007-10-25
forum: The Cafe
---

### Post by Bagboy23 on 2007-10-25
Hi guys, I'm lost and all the reading I have done on both reference theoretical stuff. I have XGL running Compiz, it's not smooth on my Mobility Radeon x700 and I get video tearing. If I move to AIGLX with the FGLRX 8.42 drivers will these problems go away of should I just leave it alone?


I've seen posts from 2006 where people say XGL is superior but recent posts show that AIGLX is on par with XGL but less resource hungry. Please advise.

:guitar:

---

### Post by ghantoos on 2007-10-25
I'm not quit sure, but i think that XGL isn't supported in Gutsy.

Can someone confirm or unconfirm this?

cheers,

ghantoos

---

### Post by sdowney717 on 2007-10-25
I moved to gutsy. I had trouble with video drivers  but now it is all fixed and works great. All my issues with linux always seem to involve video drivers. The catalyst control is buggy for ATI.

You need to get rid of xgl server. It was still loading after my upgrade.
the new ATI driver works well.
My only issue is if I run compiz then run google earth, it gives me flashing screen.
but not running compiz it is fine.

It is a pain to install ATI driver, I found many tutorials most did not work, but this one did.
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

It does what envy does and if you cant wait foir envy you can do it yourself.

---

### Post by luisromangz on 2007-10-25
For me, the 8.42 works great, but altough AIGLX is supported now, when it's enabled, all the surfaces are rendered white, so I'm sticking with XGL for a while. Maybe I didn't installed the drivers properlly, who knows. The main improvement is that rendering is now much faster.

If I were you I would give the new drivers a try, with or without AIGLX.

By the way, I'm using a (crappy) ATI 200M video card.

---

### Post by misfitpierce on 2007-10-25
eh... both give me problems with gutsy and compiz. I think compiz is not  tested enough in gutsy. Makes my videos lag when moving mouse in fullscreen video on XGL and AIGLX... So I dunno. AIGLX is better in rendering video though it had no tearing so AIGLX I guess.

---

