---
title: "Using Mixxx with more than two channels"
date: 2010-02-17
forum: Ubuntu Studio
---

### Post by Rog-Mahal on 2010-02-17
I'm using a Macbook 2,1 with an Ubuntu variant called Crunchbang, which uses straight ALSA without pulse, for what it's worth.

I bought a Berhinger UCA202 usb audio interface in order to preview tracks to beat match. The card was recognized and works automagically, but I have a snag when I try and set up the channels. If I use channels 1-2 for the output of the UCA202 to the speakers and then use channels 3-4 for the internal sound card to my headphones, I get terrible audio quality with lots of pops, skipping, and the program becomes unstable. 

However, if I use channels 1-2 for both, the problem goes away immediately, but it becomes more difficult to cue the tracks because I'm listening to the full mix through my headphones.

Does this have anything to do with latency? Or the limitations of my internal sound card?

Any help would be greatly appreciated.

-Rog

---

### Post by AutoStatic on 2010-02-18
Hello Rog-Mahal, did you try different samplerates? And what are your current Mixxx settings? And which version of Mixxx are you using?

---

### Post by Rog-Mahal on 2010-02-18
I'm using Mixxx 1.6.1, which is the version in the Ubuntu repos. No luck with different samplerates, the usb sound card that I'm using only supports 44.1kHz and 48kHz and switching between them makes no difference. 

Thanks for the reply.

---

### Post by rryan on 2010-09-18
Hi Rog-Mahal,

Could you please try out the Mixxx 1.8.0 beta? It's available from our website, [http://mixxx.org](http://mixxx.org) 

If the same problem with multiple soundcards persists, try increasing your latency in the preferences dialog. Some soundcards, especially internal ones, cannot handle low latency. If you are still having problems please file a bug in our tracker [http://bugs.launchpad.net/mixxx](http://bugs.launchpad.net/mixxx) 

Thanks,
RJ Ryan

---

