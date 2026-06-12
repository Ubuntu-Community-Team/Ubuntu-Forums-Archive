---
title: "Serval microphone is very quiet"
date: 2007-11-24
forum: System76 Support
---

### Post by TheOtherShoe on 2007-11-24
I have a laptop that is the same model as the Silver Serval Performance (model serp2). It would have been a System76 machine, except that I was in the market for a computer before System76 began offering this model.

Anyway, the problem is that the built in microphone is very quiet. It is so quiet that almost anything I record is inaudible when played back. The only thing loud enough to hear is when I tap on the microphone, or shout very close into it. But even then the sound is faint. This is the case in every application that I have tested, including Sound Recorder, Ekiga, Skype, and Team Fortress 2.

I have looked around for help on this issue. People generally recommend turning up mic boost or changing the input source. Unfortunately, I don't have a mic boost option and the only input source available in my settings is "Mic". All of the recording and output levels that I could find are turned all the way up and are unmuted. This is after searching through the options exhaustively. I noticed that a lot of the existing support for this issue is for Edgy or Feisty - so maybe some of this stuff doesn't apply since I am running Gutsy.

I have up-to-date System76 drivers installed; everything is set to use ALSA or ESD; and as I mentioned, I am running Gutsy (upgraded from Feisty).

One final detail I have uncovered is that in the Sound Preferences when I click on the "Test" button next to Sound capture I get an error message like this:
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

Are any other Serval owners having this problem? Is there anything that I can do about it? And would it be worthwhile to cash in on my warranty? Any help is greatly appreciated.

---

### Post by thomasaaron on 2007-11-26
Under the recording tab, does it have a "Digital" slider? If it does, you might want to play with that one a bit. I've noticed that it makes a difference on recording for some computers.

---

### Post by TheOtherShoe on 2007-11-26
I have played around with the digital slider. It doesn't seem to make any difference. Thank you for the suggestion.

But I did manage to improve the situation somewhat. I compiled the latest version of ALSA - which at this point is 1.0.15. That gives me a mic boost slider, which makes a big difference. By turning the mic boost all the way up and fiddling with the capture slider I can get the microphone to the point where my voice is audible when played back. There is an awful lot of crackling though; I guess that's what I should expect from amplifying a weak signal so much. At least it is working now.

Another potential solution that people are recommending is to add this line to /etc/modprobe.d/alsa-base and reboot:
```
options snd-hda-intel model=6stack-dig
```
I tried that too, but then I didn't have sound anymore. But I did notice that after adding that line and compiling the new version of ALSA I had a bunch more options in my sound preferences - and some more options for input source. So I might play around some more to see if I can make this solution work. One idea I have is to see if using a different model string helps.

---

### Post by TheOtherShoe on 2007-11-27
Ok, I have it working much better now.

> **TheOtherShoe said:**
> Another potential solution that people are recommending is to add this line to /etc/modprobe.d/alsa-base and reboot:
```
options snd-hda-intel model=6stack-dig
```
 It turns out that the reason I had no sound after trying this is that it added some new volume control sliders intended for surround sound systems, which were muted. After I turned those up, my sound worked fine. And even better, the digital slider in the capture section now affects the recording level of my microphone. The playback is still has some noise in it; but it is better than before.

If any other Serval owners are having trouble with a quiet microphone, here is the procedure I recommend (**Edit: see warning from thomasaaron below before proceeding**):

1. As is suggested above, add this line to /etc/modprobe.d/alsa-base and reboot:
```
options snd-hda-intel model=6stack-dig
```

2. Open volume control, go to Edit > Preferences, and check all the boxes that appear.

3. Make sure all of your volume control sliders are unmuted and turned up far enough for you to be able to hear sounds played through your speakers. The surround slider in particular is important to adjust.

4. In the capture section, turn the digital slider all the way up. In the input section make sure that both Input Source options are set to "Mic".

5. Fiddle with the capture slider in the capture section, and the mic boost slider in the playback section until sound played back from your microphone. The Ekiga configuration druid has a nice little tool that is helpful for this step.

6. You probably don't need to install the latest version of ALSA. But if the digital slider does not affect the recording level of your mic, or if you do not have a mic boost slider, then you will want to compile and install ALSA 1.0.15. Instructions for doing that are here: [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) . Note that in the step where you use wget to download the source packages you should remove "rc3" from all of the file names because version 1.0.15 has gone stable since those instructions were written.

---

### Post by thomasaaron on 2007-11-27
Just a note to the adventursome:

Adding model designations to the alsa-base file is risky business. I've come very close to blowing speakers doing that on numerous occasions. Most of the one's with "stack" in them are meant for Desktop computers. 

That said, during testing our shop Serval's mic was settable with OEM settings.

If that solution worked for you, that's great. We may even add it to the System 76 driver after careful testing. But I really do *not* recommend haphazardly putting model designations in there, as blown speakers are not generally covered by warranty.

---

