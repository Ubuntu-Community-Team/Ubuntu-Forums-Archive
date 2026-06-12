---
title: "Sound Card for Recording &amp; Ubuntu Studio Question"
date: 2009-12-15
forum: Ubuntu Studio
---

### Post by kemra on 2009-12-15
I've been looking for a good quality sound card recently for a new machine I'm building. All I need is a decent quality card that can be used for recording (probably via a Microphone) but it is somewhat difficult to find solid info.

I have heard that the M-Audio Audiophile 2496 is a great card and works well and I may well get one. However I have noticed that this card has been supersceded by the Audiophile 192. The only problem with this is that I cannot figure out how well supported it is in linux. The only posts I can find regarding this card in linux is to say that absically it didnt work although they were all made 2 years ago when the card was released. So bascially I'm looking for sound card recommendations.

Also another question that is related to this build. Does anyone here run a KDE desktop in their Ubunto Studio rather than the dfault gnome? If so how did you do it? Also is their any disadvantage to using KDE over Gnome in ubuntu Studio?

---

### Post by sgx on 2009-12-15
> **kemra said:**
> I've been looking for a good quality sound card recently for a new machine I'm building. All I need is a decent quality card that can be used for recording (probably via a Microphone) but it is somewhat difficult to find solid info.

I have heard that the M-Audio Audiophile 2496 is a great card and works well and I may well get one. However I have noticed that this card has been supersceded by the Audiophile 192. The only problem with this is that I cannot figure out how well supported it is in linux. The only posts I can find regarding this card in linux is to say that absically it didnt work although they were all made 2 years ago when the card was released. So bascially I'm looking for sound card recommendations.

Also another question that is related to this build. Does anyone here run a KDE desktop in their Ubunto Studio rather than the dfault gnome? If so how did you do it? Also is their any disadvantage to using KDE over Gnome in ubuntu Studio?
Hi, get an older used maudio 24/96, it will say revision 2 on the card, and in output from lspci command, revision 02.
I can not vouch for newer models. Support is kernel level, does not require deep knowledge, or strange configurations in most cases.

In the thread about E-mu 0404 usb, there has been excellent progress, and now an easy how-2 on the last page. Read there to see if you would consider such extra effort. This unit has good mic/preamp connectors built in. With the m-audio pci card, an inexpensive but excellent ART brand preamp would be good, then use the line-in to record from your mic.

There are also other good options that others use and can describe.
Cheers

---

### Post by jon armand on 2009-12-18
I have been using ubuntu since 6.10. I installed an M-audio audiophile 2496 in my PC (Intel gagl 915 main board, intel p4 3.02 GHz, 3 GB Ram). I have, however, not succeeded in making my linux daw work properly. With or without RT-kernel, the latency is far too large. (I was allowed to set the latency quite low, but once I started to record/mix/monitor, it resulted in massive x-runs).
I have tried making linux digital audio work station work, both with the audiophile 2496 and the Mobile Pre (also M-Audio), but have so far been unsuccessful.

I would certainly appreciate any suggestion that would make my life in the linux world easier!

Jon Armand

---

### Post by AutoStatic on 2009-12-19
Hello jon armand, if you need any help on improving your set up I'd suggest you open your own thread. I think there are enough forumites more than willing to help you out.

---

