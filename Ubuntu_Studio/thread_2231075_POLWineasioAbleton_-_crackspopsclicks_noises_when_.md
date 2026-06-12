---
title: "POL/Wineasio/Ableton - cracks/pops/clicks noises when playing music"
date: 2014-06-23
forum: Ubuntu Studio
---

### Post by ishaybas on 2014-06-23
[COLOR=#333333][FONT=Lucida Grande]Hi,[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I have manged to get Ableton 8 and 9 to work with POL, Jack and Wineasio with my M-audio MobilePre USB audio interface. My only problem is that when the music is playing, and I am using 128 or 256 frames per period, I get lots of cracks and pops noises. IK Multimedia Amplitube 3 on stand alone mode works perfectly with this configuration, as well as Ardour with the same Jack and audio interface at 128 frames per period.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Giving priority 99 and nice -20 to jack and the wineserver did not help resolve the problem.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]It seems as if the noises are somewhat related to changes on the screen itself, since when a window is opened or refreshed, or the level meters change faster, I can hear more noises, but there are noises even if I minimize everything and just stare at the desktop.[/FONT][/COLOR]



[COLOR=#333333][FONT=Lucida Grande]I am using Lubuntu 14.04 with LXDE, Wine 1.5.25, and the latest Wineasio from kxstudio repository - 0.9.0+git20110613-2kxstudio1.[/FONT][/COLOR]



[COLOR=#333333][FONT=Lucida Grande]Any ideas what should I be checking next?[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I am finding POL, Wine and Wineasio to be super..!!! hate to have a dual installation of Windows just for Ableton...[/FONT][/COLOR]



[COLOR=#333333][FONT=Lucida Grande]Thank you![/FONT][/COLOR]

---

### Post by gboer01 on 2014-06-25
Have you considered installing a lowlatency kernel? See my previous post at the bottom of the page:
[http://ubuntuforums.org/showthread.php?t=2227547](http://ubuntuforums.org/showthread.php?t=2227547)
Cheers

---

### Post by ishaybas on 2014-06-26
I installed the lowlatency kernel now and it definitely improves the situation a lot..!
at 128 I still get a noise here and there, but its definitely something I can work with.

Thank you!

---

### Post by CrocoDuck on 2014-06-26
Hi! You may want to try even a realtime kernel (I use it everyday) and wine-rt (never tried it). You should find them under KXStudio repos. What about your system configuration? You can optimize the whole system for audio. Have a look at [here]("http://wiki.linuxaudio.org/wiki/system_configuration"). Sometimes setting the filesystem to noatime is very effective.

---

### Post by ishaybas on 2014-07-05
Thank you, I am going through them now.
The CPU frequency change to performance already improved things very good..

---

### Post by Nistegmos on 2014-07-15
I don't know if this helps or not, but I discovered that disabling unused audio interface input channels from within the DAW software can greatly reduce CPU/disk buffering problems.  This is at least the case with REAPER v4.7.  Maybe if you find a similar setting in Ableton, it would help.  Good luck.

---

