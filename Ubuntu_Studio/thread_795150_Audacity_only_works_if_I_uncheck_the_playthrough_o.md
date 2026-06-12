---
title: "Audacity only works if I uncheck the playthrough options."
date: 2008-05-15
forum: Ubuntu Studio
---

### Post by philinux on 2008-05-15
So I can see what I'm recording but no sound, playback is just fine.

If I select the playthrough options I get stuttering and garbled sound and occasionally crash the app.

Attached screenprint shows my device selection.

I'm using a usb turntable tec-3100

---

### Post by philinux on 2008-05-15
No audacity experts around?

---

### Post by Stochastic on 2008-05-15
> **philinux said:**
> No audacity experts around?

No, anybody willing to spend the time to become an expert would usually leave that unreliable and buggy app alone. 

My only suggestion to fix your problem would be to start Jack, then open audacity.  Don't use audacity's playthrough function, but rather connect the inputs to the outputs within jack.  This solution will also give you control over the latency of the playback, should that be an issue.

---

### Post by thorgal on 2008-05-15
what is your original project ?
I find audacity quite convenient for quick reshaping of audio files but not for multitracking work. Ardour rules in this field. Audacity on the other hand can be handy at times, or Rezound as well. But ardour requires jack to be up and running properly. What about an app like traverso ? never used it but some ppl are quite happy about it. As for me, I stick to jackd, ardour and jamin, the "holy trinity" :lol:

for audacity to work with jack, you need portaudio compiled in jack IIRC. But then, jaudacity jack ports will only show up when transport is active. Maybe they can be made persistent but I never dug it because I don't care :)

---

### Post by Stochastic on 2008-05-15
Audacity has always worked with jack, no need for PortAudio.  I find it just terribly inconsistent on various issues.  And the number of tiny bugs I've run into with it have pissed me off beyond comprehension.  So now I use Rezound for my editing.

---

### Post by thorgal on 2008-05-16
is this true ? last time I used it, I had jack compiled withour portaudio support and audacity did not produce any sound. Strange ...

---

### Post by philinux on 2008-05-16
Ok many thanks for replies.

I've been given a usb turntable from my kids to record my vinyl's to cd. It works when I record and playback, sound is good. 

Thats why I needed the playthrough option to monitor the tracks.

How do you use jack with audacity or is there a better app for this project. I think I'll only be cleaning up a few old records that have bad scratches on them.

---

### Post by thorgal on 2008-05-16
I did rip some old LP's. I also have an old  turntable that I need to pre-amplify. What I did, because I did not have a preamp for it at the time (now I do but I don't rip LP's any longer), is to plug it directly to my RME Multiface II input ports, open ardour, create a stereo track, apply a software amplifier to the track, a bit of EQ and added the mastering app Jamin as an insert for boosting the overall levels. When I was satisfied with the setup, I recorded the entire thing and cleaned up for clicks and pops that are unavoidable with LP's. At the time, I did not know there was a program called gnome-wave-cleaner or something like that. So I did by hand in ardour. Really annoying but it sounded cool at the end. Finally, I divided the track in ranges (one range per song) and exported ranges after having renamed ranges to something relevant. So I got at the end a wave file per song. Then I burned a CD with K3b. That's it :)

---

### Post by Stochastic on 2008-05-16
Well to record and monitor at the same time Audacity **should** work, but it's not.  Jack can be a complicated beast to setup if things don't work right after install.  You could try installing qjackctl and starting jack before you open audacity.  Audacity **should** detect that jack is running and use it as a sound server (if not, go into audacity's sound settings and manually select Jack as your input/output device).  Now open qjackctl's connections window, and select your soundcard's input on one side then your soundcard's output on the other side, and click connect.  Now jack will be giving you a direct monitor of your incoming signal.  Audacity *may* need to be manually (through qjackctl) connected to your input if it doesn't do it for you.  There are other wave editors/recorders, but I'm not sure if any have an input monitor as usually this is done before getting to the wave editor.

On another note, if you're looking to clean up recorded vinyl, you may want to look at GnomeWaveCleaner [http://gwc.sourceforge.net/](http://gwc.sourceforge.net/) as it was built to fix LP sound issues.  It's not a recorder, so you'll still need to go through audacity or another recording app, but it could help you to clean those files up.


> **thorgal said:**
> ...did not produce any sound. Strange ...

Yup, that's audacity for ya.

---

### Post by philinux on 2008-05-17
Is rezound better for the I'm doing than audacity.

---

### Post by warbread on 2008-05-17
> **philinux said:**
> So I can see what I'm recording but no sound, playback is just fine.

If I select the playthrough options I get stuttering and garbled sound and occasionally crash the app.

Attached screenprint shows my device selection.

I'm using a usb turntable tec-3100

I believe this screen shot shows you the answer.  The end of the dialog for play-through says to turn it off for stereo mix recording.  Try setting the recording input to mono and see if that helps.  

This is just a shot in the dark as I honestly don't know.  I don't use Audacity for recording.   Rezound might be a good alternative for you.

---

### Post by Stochastic on 2008-05-17
Honestly, if you can get Audacity to work right, then Rezound vs. Audacity is a purely preference thing.  One thing I just thought of was in your Audacity screenshot there's a setting for latency.  The stuttering may be due to having a setting there that's too low for your computer; maybe try something drastic like setting it 10 times higher and see if that fixes thing (if it does then you can attempt to lower the settings until it works right).

---

