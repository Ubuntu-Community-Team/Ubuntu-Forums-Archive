---
title: "Three M-Audio Delta 1010 in Ardour"
date: 2014-08-17
forum: Ubuntu Studio
---

### Post by erik18 on 2014-08-17
Hello!
 I'm new to this. I have been working with Windows PCs for years, though.

I've installed Ubuntu Studio (14.04.1) on an SSD drive and it's running fine. I've also gotten aquainted with Ardour. 
 I need to use the three Delta 1010s at the same time (giving me 24 analog channels in and 24 analog channels out). If I open envycontrol24 I find the deltas on hw:0 , hw:1 and hw:3.

However... I've been reading up on how to make this happen and I can't get it to work. I think it is down to me not understanding how to do things. 

Could someone please give me a step by step guiding to this?

 Regards, 
 Erik

---

### Post by tgalati4 on 2014-08-17
Good luck.  Most PC's PCI buses can only handle one Delta 1010.  It has to do with timing on the bus and audio skew.  Channel 1 will have 0 delay, but Channel 24 might have several milliseconds of delay (and sound strange and out of phase).  

Pull out 2 cards and focus on getting one card to work correctly.  You need to create patches that tie inputs to outputs before you hear anything on those Delta cards.  They sound nice, but they need configuration.  They are not plug-and-play.

Once you get one card and all 8 channels recording correctly, then try a second card.  Set up the patches and try a 16-channel recording.  If you have a fast enough machine and fast enough PCI bus, you might get some tracks laid down.  I don't think you can do 24.  But prove me wrong.

[http://ccrma-mail.stanford.edu/pipermail/planetccrma/2007-December/014197.html](http://ccrma-mail.stanford.edu/pipermail/planetccrma/2007-December/014197.html)

Also, mudita24 has replaced envycontrol24 for those cards:

tgalati4@Mint14-Extensa ~ $ apt-cache search mudita
mudita24 - ALSA GUI control tool for Envy24 (ice1712) soundcards

The 24 stands for 24-bit sound, not 24 channels!  Better than 16-bit CD sound, and good for multi-track mixing.  In most configurations, you cannot monitor channels you are recording.  You have to set up a physical/analog monitor path or just don't monitor while recording.  Not convenient, but that is how the cards are designed.

---

### Post by erik18 on 2014-08-17
I've been able to handle one card. I need 24 channels out for mixing work.
 
 I run a separate disk with Win XP and have all three working well there. Sync is done with spdi/f.

 The reason I want to use Ubuntu Studio is that i really seams to free up resources. I'm just not understanding why the codes I've found online won't work for me.

---

### Post by nthomaier on 2014-11-30
Just bought a M-Audio Delta 1010LT on E-Bay because i was searching for a extendable solution for multi-channel audio recording in Adour.

My Card will hopefully arrive next week and if my PC Handles it well enough I will try with a second card and go for 16 Channels.

I was planning to follow this Tutorial. 

[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

This guy seams to have 3 Delta 1010 Cards running under Linux. 

Cheers
Semidark

---

