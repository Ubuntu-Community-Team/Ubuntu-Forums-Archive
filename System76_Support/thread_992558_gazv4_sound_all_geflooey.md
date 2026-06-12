---
title: "gazv4: sound all geflooey"
date: 2008-11-24
forum: System76 Support
---

### Post by dgermann on 2008-11-24
Hi--

Was trying to get Skype to work tonight, and now things are worse!

The immediate issue is that all sound is scratchy and broken--even the sound on login.

My system: Gazelle Value gazv4, running 8.04.1. I upgraded to the new kernel last night, but did have better sound than this tonight before I messed. Kernel now is 2.6.24-21.

I know I double clicked on the volume control in the panel. On preferences everything is checked--it was before I messed. The tabs visible are Playback, Recording and Switches.

I know I also changed some settings in alsamixer, generally moving everything up to the highest volume level.

Here is the output of amixer, if that gives some clues:
```
doug@ubuntu:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-4.50dB] [on]
  Front Right: Playback 20 [65%] [-4.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [on]
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%]
  Front Right: 2 [67%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 16 [52%] [-10.50dB] [on]
  Front Right: Playback 16 [52%] [-10.50dB] [on]
doug@ubuntu:~$ 
```

The ultimate hope is that you can help me get Skype working. I have an account I can use on my desktop system. But from this laptop when I use the call testing service, it picks up no sound at all from my end. Or more accurately, it plays back no sound at all from me. My laptop version of Skype is 1.4.0.99-1; the version on the desktop system is 2.0.0.72-1.

So what to do?

Thanks!

---

### Post by thomasaaron on 2008-11-25
First, run your system76 driver and reboot.

Second, make sure your PCM isn't turned up all the way.

Third, look in your sound control for the checkbox labeled "Ext Amp" or "Amp" or "Ext". This will completely kill sound on Gazelles. Experiment with it both checked and unchecked. (I think it should be un-checked...)

Fourth, go to System > Preferences > Sound and click the first test button. Sound? Make sure all of the drop-down selectors are set to ALSA.

Fifth, get recording and playback working in Applications > Sound & Video > Sound Recorder. Once you have the settings right for that, Skype should be easy to configure.

Sixth, in Skype, go to Options. You will need to set your Input and Output channels. If memory serves, they should all be set to ALSA.

---

### Post by dgermann on 2008-11-25
Thomas--

You are a wonder--everywhere and helpful all the time, Thomas! Thank you.

So here is what I did:

1. On System76, I chose the Restore System Tab and Restored and rebooted. Result: No real sound when the system booted back into Gnome--just a few little crackles.

2. PCM is not all the way up. Command line ran alsamixer; it shows this at 65.

Other settings: Master 94, mic 100, mic boos 67, IEC958 MM (I think that means off), Capture 100, Mix shows ------, Digital 50, External MM, Internal 52.

3. On the panel I double clicked on the little speaker icon and got "Volume Control HDA Intel (Alsa mixer). Is that what you mean? There is nothing here for external nor amp nor external amp.

The only tabs are Playback, Recording and Switches.

Going to Edit > Preferences there was an external amplifier: I unchecked that.

4. Going to System > Preferences > Sound > Devices, I made sure all drop down boxes were Alsa (most except sound capture I think) were set to "Autodetect."

The first sound test button yields a scratchy loud blaring sound, moderate pitch.

5. Went to Sound Recorder as you directed, and recorded me talking toward the screen, regular voice, then yelling. Result: nothing on the playback.

Settings: Internal Mic; CD Quality, Lossy (Ogg multimedia).

I tried to recheck the external amplifier box as above and then record again--Sound Recorder said "audio capture settings are invalid." It says to change that in "multimedia settings" but I find nothing like that in the menus. Changing it back still gives me the same error message in Sound Recorder.

Playing a video with known good sound, I just get crackles and if I listen closely, I think I can hear voices....

6. Given the results in 5, did not go to this step yet.

So is this progress? At least we know some things that do not work....

What's next, Thomas?

---

### Post by thomasaaron on 2008-11-26
Well, a few things come to mind. Turn down your master a little bit also. If it still makes that crackling when you boot up or press the test button, you might have blown speakers.

Also, 

> Going to Edit > Preferences there was an external amplifier: I unchecked that.

This one actually should be checked. When it is checked, it should cause an external amplifier checkbox to appear somewhere in the sound control panel (the window that appears when double-click the speaker icon). It's the one on the sound control panel that you want to experiment with, not the one in Edit > Preferences.

Here are my sound control settings. They are for a completely different computer and will have some different options. But it should provide a starting point. (I'm working from home today and have no GazV4 available).

I'd recommend booting from a live CD and then going to System > Prefs > Sound and pressing the test button. Is the sound still crackly? You may also want to check out the sound control settings on the live CD.

---

### Post by dgermann on 2008-11-27
Thomas--

Plugged in some external speakers and sound was OK--not crackly; on the same video, lots of crackling sound from the computer's speakers. (Same result from test sound--more like a rasp than a tone on the internal speakers--on the external it is a definite high pitched tone, and clear.) That seems to be the answer I did not want to get--does that pretty much tell us the internal speakers are shot?

Then turned down the master to about 50%. Result: could hear almost nothing; moved it up a bit from there and got clearer sound, less crackling, but still some. But not loud enough to hear the voices on the video.

Double click speaker icon in panel > edit > preferences rechecked the external amplifier box; now everything there is checked. All I have under the playback tab is Master, PCM, Microphone, Mic Boost, Internal Mic. On the recording tab, all I have is Capture and Digital. On the Switches tab, I have Microphone Capture, IEC958, Mix, Internal Mic Capture. Only the last one is checked. Playing the video, I get lots of crackling.

I don't see an attachment or anything with your sound control settings.

I will download a live CD of 8.04.1 and report back.

Assuming we agree that the speakers are shot, what's my best course of action? Do you folks do that repair work? Or can I take it to my usual computer repair people and have them put in new speakers? What kind of cost is there to be expected?

On the main issue, is it possible that the hardware microphone is not working?

Thanks, Thomas!

---

### Post by thomasaaron on 2008-11-28
I'll have to run some tests on the mic when I get back to the office on Monday.

As for the speakers, let me know what you find with the live CD. If it's the same on the live CD, your speakers are probably blown. In that case, if you are still under warranty, or want me to get a quote for you, please fill out this form...

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

If you are out of warranty, you can also take it to a local repair shop. Prices would probably be comparable, but the repair shop might be quicker.

---

### Post by dgermann on 2008-11-29
Thomas--

OK, tried the live CD. Initially, I got no sound at all when I clicked on test. Then I went to the speaker icon, double-clicked and under edit > preferences I checked all but the IEC958. Then I re-ran the test sound and still got the crackly sound.

I also tried running a couple of the example sounds and videos provided on the disk: all were crackly and unintelligible.

Sounds like the speakers are blown. Do you agree?

Some really basic questions: 1. How long is the warranty? I have had the computer since about September, 2007. I will have to see if I can find the box it came in....

2. Where do I find the serial number? On the bottom is a silver sticker with a model number S62FM and below that on the same sticker is a long string starting with 75NOAC. Above that, on a panel held by two screws is a barcode with a number starting AS17.

I might just be better off sending it to you so you can get the microphone working. Unless you think we can somehow test that with it in its current condition.... What do you advise, Thomas?

Thanks for generously helping so much!

---

### Post by thomasaaron on 2008-12-01
Definitely sounds like blown speakers.

Please fill out this form (it has info about the serial number). It will get sent to my email. I'll then send you further instructions.

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

---

### Post by dgermann on 2008-12-01
Tom--

OK, have filled in the form.

You mentioned testing speakers when you got back in on Monday. Do you think that is something I can do on my end, or do I need perhaps a hardware fix on that as well? Remember, I can plug in external speakers and do some testing with the microphone before making a decision whether I need to ship it off to you.

Thanks for you help Tom. You make customer service sing...and dance! :guitar:

---

### Post by thomasaaron on 2008-12-02
If your internal speakers are crackling (and your PCM is not turned all the way up), but external speakers to not crackle, you most likely have blown speakers -- especially if they do this from a live CD.

As for your mic, that most likely is a configuration issue in your sound controls. I'll definitely try to test that here in the shop and post some screenshots, but, in essence, you just need to play around with the settings. I *believe* on the GazV4, 'Front Mic' is the external mic and 'Mic' is the internal mic -- but I could have that backwards.

--------------

EDIT: Actually, looking over my whiteboard, there was an unresolved recording bug on the GazV4 in Hardy. My first step would be to test recording from an 8.10 live CD to see if it was fixed under Intrepid.

---

### Post by dgermann on 2008-12-02
Tom--

Many thanks. Via email I have asked you to begin the paperwork for getting the new speakers. Still wonder what I did to blow them out!

Let me know what you figure out about the recording bug and the mike. If it is a recording bug, then I should be able to get Skype working and ignore the recording issue, yes?

---

### Post by thomasaaron on 2008-12-03
It depends, really. We'll have to do some testing on it. I'll report back with my findings.

---

### Post by dgermann on 2008-12-06
Tom--

Great! Let me know what you find out about the microphone--maybe I can get that working before I send the machine back for service on the speakers....

---

### Post by dgermann on 2009-04-05
Tom--

OK, now that the computer is back with the replaced speakers, may we proceed to getting the microphone to work? 

You said you were going to run some tests, thinking that there was a problem with GAZV4 and 8.04.1, which you thought might have been fixed in Intrepid....

Here is what I did today:

1. System > Admin > System76 > Restore System; also install drivers; reboot

2. Checked PCM—not all the way up; command line alsamixer shows it at 65%

3. panel > speaker icon > edit > preferences > unchecked external amplifer

4. system > preferences > sound > first test button = good sound; reset next to last (sound capture) from PulseAudio Sound Server to Alsa mixer; clicked on test and got nothing. Only the “test sound” choice here produces any response

5. Applications > Sound & Video > Sound recorder; tried all the input methods; only Capture and mix produced anything, and it was white noise, barely audible.

6. Checked Tom Aaron's post # 4 here, and rechecked external amplifier (now everything here is checked)

7. Then went back tried sound recorder—with external amplifier unchecked, I get white noise (louder now) on all but internal mike (which is what is checked on the volume control).

There is a thread here (see post #1) that suggests that most sound problems are not settings but drivers. [http://ubuntuforums.org/showthread.php?t=385739]("http://ubuntuforums.org/showthread.php?t=385739")

OK, my topmost guru, what next? (I sure hope the mic is not blown!)

---

### Post by thomasaaron on 2009-04-05
Hi, Doug. 

It's been a while since I ran my tests. If memory serves, I couldn't get the internal mic to work, but I could get an external mic to work.

Is that what you're seeing? Or can you not get either to work?

Also, are you opposed to upgrading to 8.10 if that will solve the problem? Just wanting to know the best place to focus my efforts.

---

### Post by dgermann on 2009-04-05
Tom--

Glad you're still watching this old thread.

You are right, Tom, the external mic does work--although it is very scratchy and jumpy.

I don't like the idea of moving this machine to 8.10 or even 9.04 when that is out, because I have 4 other machines on 8.04.1 because it is lts. Those are desktop boxes. (On at least one I am able to use Skype.) The other issue of course is that commits me to upgrading more often than the lts boxes, too.

So if you are clear it works on 8.10 and there are not other reasons to avoid it, I will make the jump, even though I'd prefer to stay.

One other thing: since I have been playing with the settings, my playback volume is low and hard to hear. Any suggestions what I should be adjusting there?

---

### Post by thomasaaron on 2009-04-09
Hi, Doug.

OOOOOPS! I missed that you were on 8.04. Let me re-tool.

---

### Post by dgermann on 2009-05-07
Tom--

Any progress?

---

### Post by thomasaaron on 2009-05-07
Somewhat.

I can get the external mic to work with 8.04. I cannot get the internal mic to work.

Loading up Intrepid.

---

### Post by dgermann on 2009-05-07
Tom--

Thanks!

Or would it make sense just to jump to 9.04?

---

### Post by thomasaaron on 2009-05-08
Actually, I meant Jaunty, not intrepid. I should have some more results by C.O.B.

---

### Post by thomasaaron on 2009-05-15
I tested with Jaunty to. No internal mic. I tried several model designations in alsa-base, but to no avail. Still testing.

---

### Post by dgermann on 2009-05-16
Tom--

Given that the problem exists across OSes, could it be a hardware issue, or something to do with BIOS? Can we be sure the internal mike works at all?

Just thinking out loud....

Thanks, Tom, for continuing to help me with this.

---

### Post by thomasaaron on 2009-05-16
Yes. It works on my machine with Feisty. It worked in Hardy too, until a dreaded update came down the pike. That was the last it worked, and I can still make it work using an older Hardy live CD. 

It's definitely a regression in ALSA. We're gonna have to file a bug with ALSA on it (or find a model designation for the alsa-base file that works). Given how long it's been broken, I doubt any future versions of ALSA will fix it without a bug report.

---

### Post by dgermann on 2009-05-17
Tom--

OK. Let me know when you have something figured out!

---

### Post by dgermann on 2012-01-04
Tom--

Wondering if you will see this old thread.

Just tried to use sound recording today on the same laptop. We are now on 10.04 on this gazv4.

Still not able to record, nor use Skype 2.2.

Is there any fix for this? Did you file a bug with ALSA?

Thanks, Tom!

---

### Post by isantop on 2012-01-05
Looking at this, you may have a hardware problem you your specific machine. I'm not sure how many GazV4s we have out there, but we haven't had any reports of it.

Tom has actually moved on to his own company, and this issue was handled before my time here. I'm afraid I don't know where Tom was at with this case, as I don't have any of his notes on it.

---

### Post by dgermann on 2012-01-05
isantop--

Thanks for getting back to me. Sorry to lose Tom, but I have learned that you are as responsive as he, which is saying a lot of good!

So is there some way of testing the microphone to see, other than what we have already done?

And is there perhaps some cheaper way to resolve this than shipping the unit back to you? For instance, I wonder if there is a decent microphone I could just add on, or perhaps if one would come with a webcam (it would be nice to add a webcam)? I will do some poking around on that, too, but if you have a place you'd look, please let me know.

Thanks!

---

### Post by isantop on 2012-01-06
An external Mic is definitely a possibility, and would probably be fairly inexpensive. I know there are some webcams with microphones built in, but they tend to have iffy sound quality, at best. I would recommend a dedicated external mic anyway, since it will have decent sound quality, and most are very cheap; around $10-$15.

---

### Post by dgermann on 2012-01-08
isantop--

Thanks! Makes a lot of sense! I will check them out.

Thanks, isantop!

---

