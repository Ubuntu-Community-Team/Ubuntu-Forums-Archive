---
title: "Audacity problems"
date: 2009-01-08
forum: Ubuntu Studio
---

### Post by Jameshardy88 on 2009-01-08
Hi, ive been having a few problems with audacity. When i record i get this high pitched squeel sound in the background. With a bit of research i discovered that this was probably because audacity uses OSS sound driver whereas ubuntu uses ALSA by default. so i followed the advice i found below.

------
March 28th, 2007, 05:22 AM
I had a similar issue. When I tried to record in audacity it would have crappy quality and a hiss. It took me forever to figure it out, but I eventually found a link on the audacity site which explained it. My understanding is that audacity uses OSS sound driver by default and ubuntu uses ALSA by default. Assuming this is the problem, all that you have to do is go to synaptic and search "aoss", without quotes. Then download alsa-oss.
Then go to your terminal and type "aoss audacity". Then double click on the volume control, which is on the top bar of the screen by default. then click on the capture tab, and make sure the recording volume is up. Then test out recording in Audacity!
-----

this did seem to sure the sound problem whilst recording (sound waves were different) however it will not let me listen to the result as the program just crashes when trying to playback the results. Has anyone got any ideas why this may be and how to fix it?

thanks for any help, James

---

### Post by ajgreeny on 2009-01-08
This could be a totally different situation to yours, but my computer has two microphone input sockets, one at the back and one at the front.  If I use the back socket with my mic, all is well, but if I plug the same mic into the front socket there is so much background noise and hiss that it is totally un-usable, with exactly the same audio settings, just the socket in use being different.  Apart from that there is no problem with audacity for me, it works very well, better than in windows, in fact, though my windows sound quality was always dreadful, so that was expected.

---

### Post by CharmlessMan on 2009-01-11
Ok I got a question that's been asked before but I saw a thread with no answers.

Audacity won't recognize my USB mic. It recognizes the other non USB one but records very low & has a hissing noise.

How do I get my USB one to work?

---

### Post by CharmlessMan on 2009-01-23
Damn nothing? REally? I've searched various threads & don't wanna start a new one. My non USB mic is also recording low.Everything volume wise is set to the highest. I really need help :/

---

### Post by x C0MMAND0 x on 2009-01-25
> **CharmlessMan said:**
> Damn nothing? REally? I've searched various threads & don't wanna start a new one. My non USB mic is also recording low.Everything volume wise is set to the highest. I really need help :/

For low mic recording volume, you could check out 

[http://ubuntuforums.org/showthread.php?t=1048568](http://ubuntuforums.org/showthread.php?t=1048568)

and see if you could use that workaround.

---

