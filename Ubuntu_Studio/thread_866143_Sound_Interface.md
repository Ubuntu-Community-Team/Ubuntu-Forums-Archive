---
title: "Sound Interface"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by ringoShells on 2008-07-21
Anyone know a decent one that is reasonably hassle free in getting running in Ubuntu (or ubuntu studio...if theres much of a difference)?

I was looking at a [Line6 Toneport UX1]("http://line6.com/toneportux1/") but I read plenty of people having hassles.

Anyone got any ideas?

---

### Post by Stochastic on 2008-07-21
There are TONS of great interfaces that work really well, but I think a bit more info from you is needed before a good recommendation can be made.

First, are you looking to buy it for a laptop or a desktop box?
Second, what's your price range?
Third, will you be doing much vocal recordings (or to phrase this differently, will clear mic-preamps be a selling point for you)?
Fourth, how many ins/outs are you looking for?

Line 6 do not give their specs out to developers (i.e. to the Linux community), however some of their devices are fully USB standards compliant chips.  What this means is that for those standards compliant cards there is full compatibility in Linux (thanks to the alsa drivers), but for the others you're SOL.  Your best bet is to find a company (such as m-audio, echo, or focusrite) that are more receptive to open-source driver development (m-audio's firewire series, however, is not supported).

If you're budget is around the $100US mark (about what the card you mentioned costs), then your best bet is to look through the alsa supported soundcard list [www.alsa-project.org](www.alsa-project.org) for something USB or CardBus driven (assuming you're on a laptop).  To compete feature-for-feature with the Line6 card you mentioned, I'd point you toward the M-Audio lineup.  You could also get a cheap firewire card (firewire is a better communication protocol for audio applications) provided it's listed as supported (or at least 'reported to work') in the device support page of [www.ffado.org](www.ffado.org) but a card such as the Echo AudioFire2 (much better quality than the Line6, but with vaguely similar features) will cost approx $200US.

Anyways, if you give more details, we can get more specific.

---

### Post by ringoShells on 2008-07-21
1. Laptop. Dell Inspiron 6000. 
2. Depends on the decency of the interface really. I probably wouldn't go far beyond $200US though. It'd all depend on value for money and quality really.
3. Yeah...plenty of vocals.
4. I'm not certain...again that would have a lot to do with cost versus quality.

thanks for the advice.

---

### Post by Stochastic on 2008-07-22
This webpage may be of interest to you: [http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

But the alsa and ffado driver support listings are your best reference.

---

### Post by ringoShells on 2008-07-23
thanks for that.

---

