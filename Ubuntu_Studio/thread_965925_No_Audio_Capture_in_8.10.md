---
title: "No Audio Capture in 8.10"
date: 2008-10-31
forum: Ubuntu Studio
---

### Post by DrRockso on 2008-10-31
Hey Daddy-O's, Dr. Rockso here...

Just upgraded one computer to 8.10 and did a fresh install of 8.10 on another computer, both were running 8.04 before, and both were able to capture audio/record before without issue.

In 8.10, my settings are exactly the same as they were in 8.04, but I cannot capture audio now. I do have sound playback, just no capture.

I have an Audigy 4 in one and Audigy 2ZS sound card in the other.

I have already gone into the Volume Control/ALSA Mixer and everything for Recording was muted, so I unmuted them, and tried again, no luck. Then I opened the Volume Control/ALSA Mixer again, and found it muted everything again on it's own under Recording. After repeated attempts it keeps doing that. 

So I went to System > Preferences > Sound and everything is as it was before, but when I do the tests, the sound capture device makes no sound, locks up and crashes during the test.

I have gone into my BIOS's to double check settings and make sure there is no conflict between the onboard audio and the cards I have installed, all is good there.

I was going to try asoundconf but others on this forum reported that they lost audio completely when they did that.

My sound card is detected, plays back audio, and has all the options in the mixer, it simply does not want to capture audio.

And yes, Dr. Rockso's speakers are on ;)

Can anyone help out a poor old Rock N' Roll Clown? Who's got some help for Dr. Rockso? Cooka-yayah-o!

---

### Post by DrRockso on 2008-11-01
**workaround removed, no longer works after updates**

---

### Post by kylea on 2008-11-05
Ok did all this and got Skype to work. So thanks for the post.

Not sure this is the final answer - will go home and try a few other record functions.

Have noted that the All the mike icons are muted on the Volume Control "Recording" Tab - not sure what that means?


Regards

Kylea):P

---

### Post by DrRockso on 2008-11-05
Sure, no problem, glad Dr. Rockso could help. :guitar:

All my icons in the volume control > recording tab are muted too, but all my recording functions are working since I did the fix. If I open a terminal and enter: **alsamixer -V all** all those same items are not muted in there. Weirdness.

If you come up with/find/learn anything, please let Dr. Rockso know! :KS

---

### Post by kylea on 2008-11-05
Its hard to be critical as the developers do this work for no $$, however its is very frustrating to make the jump from XP and Microsoft and have to struggle with stuff like this.

It seems to me that we have a two stark choices - software that initially works very well but eventually fails because its foundation is so poor - or software that is exciting and built on a solid foundation, but none-the-less also causes grief though a lack of superior QA.

It may be Beta software but it should suffer the level of regression that I have experienced.:confused:

---

### Post by raedbenz on 2008-11-05
thanx for the solution. NOw i can ring others and hear them but others cant hear me (the mic doesnt work) any hints????
i hope that there is gona be a new Skype release to work without all these settings on Ubuntu8.10

---

### Post by DrRockso on 2008-11-05
> **kylea said:**
> Its hard to be critical as the developers do this work for no $$, however its is very frustrating to make the jump from XP and Microsoft and have to struggle with stuff like this.

It seems to me that we have a two stark choices - software that initially works very well but eventually fails because its foundation is so poor - or software that is exciting and built on a solid foundation, but none-the-less also causes grief though a lack of superior QA.

It may be Beta software but it should suffer the level of regression that I have experienced.:confused:

Hey kylea,

 I understand your frustration, but keep in mind that the Ubuntu team (and those who develop software we run on Ubuntu) tend to fix things like this rather quickly. I'm sure the Ubuntu Studio crowd are making some noise about this too. I have full faith that this issue will be fixed soon, in the meantime I hope you can get by with the fix I found.
Look at it this way, with Windows you pay for those headaches, if you get a headache with Ubuntu, at least you didn't pay for it. ;)

No operating system is perfect, they all have their flaws, as you know.

---

### Post by DrRockso on 2008-11-05
> **raedbenz said:**
> thanx for the solution. NOw i can ring others and hear them but others cant hear me (the mic doesnt work) any hints????
i hope that there is gona be a new Skype release to work without all these settings on Ubuntu8.10

No problem raedbenz, glad I could help. Hopefully the Ubuntu team can fix it so no one has to do this work around anymore.

If you open a terminal and enter: alsamixer -V all

Do you see anything muted in there?

Reference: [http://en.wikipedia.org/wiki/Alsamixer](http://en.wikipedia.org/wiki/Alsamixer)

---

### Post by ipburbank on 2008-11-23
None of these fixes seem to be working for me, although when ever I like scream into the mic, I can kinda hear myself in a groggy chirp in the skype playback recording. I can hear myself fine in the realtime playthrough, but can't seem to record, which for me is bad because I use this machine to make podcasts and video tutorials.... which don't work without sound... If anyone has a quick fix that would be great!

~thanks guys and gals - Istvan, creator of All Free VFX

---

### Post by DrRockso on 2008-11-23
I hear you, I use Ubuntu for all my audio and video work, so this has been a real pain. Between the sound capture and the borking of ffmpeg, I have lost a lot of time.

Only other thing I can think of is...

Go to: System > Administration > User and Groups

Click on "Unlock" and enter in your password.

Click on the "User Privileges" tab, and make sure everything you would need in that list is checked for audio and video, for me, I have everything in that list checked.
Just in case...re-enter in your password by hand in that first tab, then close that window.

Now reboot and see if that gives you better access and control.

---

### Post by Delkster on 2008-11-23
I'm not sure if mine is exactly the same problem, but I used to have audio recording working, and now it isn't. The sound card is a SB Live (emu10k1).

Interestingly, though, it did work when I tried it a few weeks ago, also on 8.10. Now everything still seems to be okay except that no input from the microphone is captured. No sign of why this happens.

I did the stuff mentioned in this thread a long time ago when originally setting things up (unmuting capture, selecting mic as the capture device, and I also nuked pulseaudio shortly after upgrading to 8.10 and a lot before the previous successful attempt). I went through the ALSA settings again just as a check, and they seem to be okay. I can also get real-time playthrough if I unmute the output channel for the mic and crank the volume up.

I tried in Audacity, and I tried in the GStreamer sound properties tool as well as other GSteamer-based applications. No go. I noticed that libasound-plugins had been updated some time ago (perhaps between the successful and unsuccessful recording attempts) and tried downgrading it, but that didn't seem to have any effect. FWIW, I also tried an older kernel (although of a different flavour -- I happen to have an -rt kernel installed also, and that hasn't got the recent updates that the -generic variant got, so I tried it).

The microphone itself physically works, as evidenced by playthrough, and also the fact that it works in a different system (still running 8.04). It also works on this same computer if I boot a 8.04 live cd instead, so the sound card should also be okay.

I'll keep trying to figure out what's going on. There were some audio applications that I installed between the cases of success and failure, and that might have included stuff like jackd, but I got rid of that already, too. I'll see if there's anything else that might have an effect.

---

### Post by DrRockso on 2008-11-23
I have a laptop that sounds like it has the same issue as your computer with 8.10. My work arounds worked for all my other computers, but not that laptop.

If you discover anything please let us know!

---

### Post by DrRockso on 2008-11-24
I just installed some updates from proposed, and it totally wiped out my ability to capture sound again. PulseAudio was one of the updates along with some related packages.

**UPDATE:** I have "upgraded" to Hardy from Ibex ;) , which after install you get prompted to do updates, and when you do they also kill sound capture ability, but unlike Ibex there is a way around it. In Hardy go to System > Preferences > Sessions then uncheck the box for Pulse Audio, then create a **killall pulseaudio** startup command in Sessions. Then go into System > Preferences > Sound and set everything to ALSA. Now reboot, and after reboot, in a terminal run: **alsamixer -V all**and make sure nothing is muted, toggle the m key on your keyboard to mute/unmute, and make sure all levels for volumes are where they should be.
This is a very ugly workaround, but it works.


"Upgrading" to Hardy also solved the ffmpeg nightmares for me too.


I hope that the Ubuntu crew can make Ubuntu stable again for sound capture and video encoding, I bet the Ubuntu Studio guys are a little frustrated.

---

### Post by mgangav on 2008-11-24
> **DrRockso said:**
> 
Look at it this way, with Windows you pay for those headaches, if you get a headache with Ubuntu, at least you didn't pay for it. ;)


I'm going to remember that!

---

