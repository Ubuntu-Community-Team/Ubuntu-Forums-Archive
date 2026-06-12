---
title: "ardour + aeolus"
date: 2011-06-08
forum: Ubuntu Studio
---

### Post by besser_dark on 2011-06-08
Hello all. Excuse me for my english. This text I translated using Google translator.
I have a big problem with the Jack server because I have a lack of experience.

What is the principle compound in the Jack server applications and how to connect ardour + aeolus (with midi virtual keyboard) in real time?
 Can I connect on the same principle Rakarrack or SooperLooper. I mean, midi keyboard + Rakarrack / SooperLooper + ardour?

 I already got to write the sounds in Audacity from aeolus, but Audacity lags a bit and the system works hard.

 Computer Configuration:
 Intel Pen Seleron 2,8 Ghz
 1 Gb RAM
 ATI Radeon 3650 512 mb
 Hard Drive Seagate 80gb (old xD)
 OS: ubuntu studio 11.04

&#1047;&#1072;&#1088;&#1072;&#1085;&#1077;&#1077;, &#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;

---

### Post by sgx on 2011-06-08
photos of common connections: 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

cheers :)

---

### Post by besser_dark on 2011-06-12
I suddenly had an idea. Maybe I is not worth installing ubuntu studio 11 on this configuration? How do you think?

---

### Post by Flaggmann on 2011-06-13
Some programs are automatically aware of jack and will show up in the connections window when they are started. Other programs you have to tell them to look for jack or operate using jack. Usually these programs have an option in one of the menu items to enable jack; once enabled these programs will also show up in the jack connections window when started. Some programs won't show in the connections window until you actually hit the play button in the player as well. 

Sometimes pulseaudio and alsa will conflict, and if you need to use alsa you need to disable pulse. Be careful here, as this will also take away the desktop as well. The best way I have found to disable pulse audio is do a google search for "disable pulseaudio elegantly" and follow his few steps; he includes copy paste terminal strings to reverse the process as well. Basically he disables pulse, then fools the OS into thinking it is still there so it will not attempt to restart itself.

There is a pulseaudio-jack lib I think, however, the problem arises between Alsa and pulse when it comes to which one grabs and holds the soundcard hardware resources.

I run alsa and jack only and have pulse disabled using his method, but the negative here is some programs, like mythtv are setup to use pulse. They either will cancel the pulse disable process or else won't work without pulse for audio portion.

multiple instances of jack can be run now to allow use of multiple sound cards, but haven't got that far yet.

---

