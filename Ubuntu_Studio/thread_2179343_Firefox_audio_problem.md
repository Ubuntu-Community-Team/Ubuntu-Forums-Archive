---
title: "Firefox audio problem"
date: 2013-10-07
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2013-10-07
This is the first time i have posted in Ubuntu forums,

I am running Ubuntu Studio 13.04, with all of the most recent stable software updates, kernel updates, images, etc...
The applications involved here are Firefox(latest version), Ardour, Hydrogen, Rackarrak, and possibly QjackCtl.

Basically here is my problem

I can boot my computer, open firefox, and everything works fine. Nothing is wrong with the audio at this point.
However i do a lot of studio recording with this machine.
I open any other application (i.e. Ardour), and that application also works fine. But once i open that application, or any other application,
the audio in firefox refuses to work.
I have tried using QjackCtl, audio mixer, and PulseAudio volume control to fix this issue and none of them seem to be working. 

I am almost clueless when it comes to QjackCtl (i do basic things with it)
When i go into audio mixer, everything is on, nothing is muted.
When i go into PulseAudio, everything is at 100% and unmuted.

The only way i can fix the problem is by rebooting the computer, which is quite a hassle just to watch a 3 minute video. 

Keep in mind this is my first time using the forum so please no hate on how awful my description is :confused:



Edit: After some updates to Firefox, and all of the Ubuntu studio security updates, more problems occour.

I can start Firefox before starting any other "audio production" software, and the problem stated in the above section still persists;
however, since the updates, it also happens in reverse. Once Firefox opens, no other "audio production software will work. 

So basically i have to decide "do i want to make music today, or use Firefox?"

---

### Post by jejeman on 2013-10-08
>  So basically i have to decide "do i want to make music today, or use Firefox?" Yes. After you accept that, you can find the ways for them to work together.
You need to read this, if you haven't already
[http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)
to start approaching your problem which we have all faced. And learn to accept > no youtube while JACK is running.
Unless > you have 2 soundcards, pray for pulseaudio-jack-sink to work, run JACK all the time and configure ALSA to play everything with JACK, download video and watch it in JACK aware player.
>  The only way i can fix the problem is by rebooting the computer, which is quite a hassle just to watch a 3 minute video. That is not necessary after you understand what is going on.

---

### Post by Tristan_Williams on 2013-10-08
Thanks. That got me on the right track to fixing my problem.

---

