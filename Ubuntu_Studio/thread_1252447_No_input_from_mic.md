---
title: "No input from mic?"
date: 2009-08-28
forum: Ubuntu Studio
---

### Post by kizile on 2009-08-28
Hey. ive been having an issue with my mic jack. I have been using JACK to bridge my audio connections from hydrogen to ardour, and it works easily. the next step i want to take is to record my electric keyboard via an aux cable from the keyboard to my microphone jack on my mobo. (motherboard is a shitty ASUS one with the realtek sound card) Now my problem is as follows.

I have it all hooked up, aux cable into 3.5 to ?? converter into the back of the keyboard and the pc. When i play on the keyboard it comes through my desktop audio, even when on the ubuntu login. I cannot for the life of me, however, get any applications to pick up the audio from the keyboard. JACK shows that i have 2 inputs, one fails to connect and the other is silent. I am quite confused as to why i cannot pick up any audio in an application. Not even sound recorder. I can play it, but the spectrum analyzer thingy just stays flaccid. Help?

Thanks.

---

### Post by kizile on 2009-08-28
oh, im on 9.04 if that helps.

---

### Post by wildnfree on 2009-08-30
> **kizile said:**
> Hey. ive been having an issue with my mic jack. I have been using JACK to bridge my audio connections from hydrogen to ardour, and it works easily. the next step i want to take is to record my electric keyboard via an aux cable from the keyboard to my microphone jack on my mobo. (motherboard is a shitty ASUS one with the realtek sound card) Now my problem is as follows.

I have it all hooked up, aux cable into 3.5 to ?? converter into the back of the keyboard and the pc. When i play on the keyboard it comes through my desktop audio, even when on the ubuntu login. I cannot for the life of me, however, get any applications to pick up the audio from the keyboard. JACK shows that i have 2 inputs, one fails to connect and the other is silent. I am quite confused as to why i cannot pick up any audio in an application. Not even sound recorder. I can play it, but the spectrum analyzer thingy just stays flaccid. Help?

Thanks.

I have the same problem with 9.04

I have searched the forums and found this question raised in the past but never answered. I tried the irc channels and got the information that the sound is broken in Jaunty, and the entire stack has been re-written for Karmic (from Mackenzie Morgan on #ubuntu-women). It was suggested I could try ensuring my uid was in the right audio groups, but that didn't help.

The problem does appear to be a permissions issue. But I have so far not found any fix for it.:confused:

---

