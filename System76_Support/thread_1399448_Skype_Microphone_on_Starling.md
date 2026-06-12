---
title: "Skype Microphone on Starling"
date: 2010-02-05
forum: System76 Support
---

### Post by macabrem on 2010-02-05
Has anybody had any luck getting audio in Skype to work on a Starling running 9.10 Netbook remix?  I've tried to follow some of the instructions on this thread, but have had no luck:

[http://ubuntuforums.org/showthread.php?t=1364747&highlight=skype](http://ubuntuforums.org/showthread.php?t=1364747&highlight=skype)

It doesn't appear that the older versions of Skype are available to download anymore.  

I've even tried the following code - but it didn't seem to provide any functions that made the internal mic work any better with Skype.
"sudo apt-get install padevchooser pavucontrol"

I can get the video to work, but the most I can get out of the audio is almost whisper levels with the audio turned way up on the receiving computer.

---

### Post by macabrem on 2010-02-06
[FONT=monospace]I got this to work, but I had to get the older Skype program from a non-skype source.  I just googled the package and used the first download link I found.  

It's too bad that the newest Skype doesn't have the microphone controls needed to get it to work with Ubuntu 9.10.
[/FONT]

---

### Post by riseringseeker on 2010-02-26
> **macabrem said:**
> [FONT=monospace]I got this to work, but I had to get the older Skype program from a non-skype source.  I just googled the package and used the first download link I found.  

It's too bad that the newest Skype doesn't have the microphone controls needed to get it to work with Ubuntu 9.10.
[/FONT]

Sorry for the late reply, but though I don't have a Starling, I have had skype (from the skype site) working fine on a 9.10 install on 2 System76 computers.  I have not tried the 32 bit version, but can tell you that the 64 bit version runs fine.

The latest beta skype even solves an annoyance with the earlier version, I now have the "ring" over the speakers while the conversation goes over the headest.  Prior to this, it was one or the other.

9.10 uses pulse of course, I'm not going to argue the merits of it vs. ALSA, just they are different.

To get the microphone controls that are "missing" in 9.10, do this in a terminal:

```
sudo apt-get install pavucontrol
```

or of course you could get it from synaptic, or the Ubuntu Software Center, it's under Sound and Video, listed as "PulseAudio Volume Manager".  I have no clue why that's not installed by default, but it isn't.  From the terminal, this will also install PulseAudio Device Chooser, would guess it would if you install it from USC, or Synaptic...

Open the Pulse Audio menu item under Sound and Video, and it will allow you to choose which input and/or output to use.  You can even choose to have it "fall back" to a device, handy if you don't always have the headsets plugged in for example.

Any questions, just ask here, or send a PM if you prefer.

---

### Post by PatrickVogeli on 2010-02-27
You can also try something:

get the latest skype for linux from skype.com and, after installed, open a terminal and launch skype this way:

/bin/sh -c "PULSE_SERVER=127.0.0.1 /usr/bin/skype"

Not the same machine, of course, but in my Acer 1810TZ I had terrible mic performance (static crackling noises) when using skype and, after this, it works fine.

---

### Post by vttay03 on 2010-02-27
I know this doesn't help a lot but I was able to get it working out of the box without any mods (the newest version up on Skype's website).  However, I noticed that my voice was fading in and out and went searching around the preferences and found an option that said "Allow Skype to automatically adjust mixer levels".  After I unchecked it, I sounded a lot more consistent.  I'm running UNR 9.10 on my Starling.

---

### Post by thomasaaron on 2010-03-01
mcabrem,


The current version of Skype should work. You may have to kill pulseaudio for the mic to work, though.

Are you using 9.10? What version of Skype to you currently have installed?


Where are you on this, and what have you tried already.

---

### Post by macabrem on 2010-03-02
> **thomasaaron said:**
> mcabrem,


The current version of Skype should work. You may have to kill pulseaudio for the mic to work, though.

Are you using 9.10? What version of Skype to you currently have installed?


Where are you on this, and what have you tried already.

Tom,
   Thanks for responding.
 
   When I originally posted, I was using the newest version of Skype (whatever # that was 3 weeks or so ago), and 9.10 regular Ubuntu.  

   I can't give much more input on this right now since I'm using a different Linux distro right now - using the older version of Skype still.  I might experiment with 9.10 again soon.

  Thanks again for the response.

---

### Post by bvandev on 2010-03-05
Thomas can you please confirm you have Skype working on a Starling?  I have tried several times with no success.  You mentioned in this tread killing pulseaudio.  I tried that and was left with no sound at all.  Could you be more specific?

Riseringseeker has suggested in a few of the threads that installing pavucontrol and making appropriate setting adjustments can solve the problem, but I don't believe he tried that on a Starling.  When I tried that, there were no settings in the pavucontrol screens that helped.

For now I'm still running vertion 2.0.0.72-1.  So I'm fine.  But that version does not appear to be available for download anymore.

Vttay03, it would be interesting to know which version of Skype you have loaded and what settings you have in place.

Thanks.

---

### Post by thomasaaron on 2010-03-05
I'm loading Skype on a Starling running UNR 9.10 now.

---

### Post by thomasaaron on 2010-03-05
OK, I tried downloading Skype from Skype.com (the 8.10 32-bit version). (It looks like Skype has stopped developing versions optimized for Ubuntu.)

It didn't work.

I also tried downloading the Pulseaudio volume control pavucontrol, and that did not work either.

I'll try to find an older version of skype to test with.

---

### Post by vttay03 on 2010-03-05
I'm running the newest version up on Skype's website - 2.1.0.81.  I searched around forever to find the older version but couldn't find an active link (I think the previous version was 2.0.0.72 or something like that).  However, after installing 2.1.0.81, everything worked pretty much out of the box.  The only problem I've had is with other users complaining my video can be choppy at times.  I'm using pulseaudio and didn't have to install pavucontrol.  Below is the audio portion of my config.xml file:

```

  <UI>
    <CaptureDevice>PulseAudio server</CaptureDevice>
    <RingDevice>PulseAudio server</RingDevice>
    <SoundDevice>PulseAudio server</SoundDevice>
  </UI>

```

---

### Post by thomasaaron on 2010-03-08
vttay03, is that on a Starling?

---

### Post by vttay03 on 2010-03-08
Yes, I'm on a Starling running UNR 9.10.

---

### Post by thomasaaron on 2010-03-08
Could you please post screenshots of your Skype and sound settings?

---

### Post by vttay03 on 2010-03-09
--Screenshot of audio settings for Skype running on a Starling with UNR 9.10 installed is attached.  Let me know if you'd like any other screenshots.  I'll be happy to provide them.

---

### Post by ants280 on 2010-03-09
Hello all, I received a System76 Starling in the mail last week.  Uh, yeah...

I have been trying to get my microphone to work with Skype.  The sound and video are working fine (actually great!)  The only problem is that I am getting no sound.  

It wasn't until the other day that I realized that the reason Skype not getting any sound input was not Skype's fault.  I cannot get any sound to input via the microphone for any program.  

I have tried installing "pavucontrol" (as prescribed by a Skype thread), and have reinstalled alsa-utils alsa-base and linux-sound base (Reinstalling them on my desktop installs my missing soundcard when a new Linux kernel comes out).  When I boot off a Karmic Desktop LiveCD, the input shows two microphones, a "Microphone 2" which gets no sound, and a "Microphone 1" that gets some sound, but is very muffled.  

Does the microphone work for 9.04 or 8.10?  I know System76 just started shipping 9.10 on their Starlings and I understand how some of the drivers may not be supported/nonexistent.  I don't mind using older distributions or the Desktop version rather than the netbook remix of Ubuntu.  I view the microphone as a very important piece of my netbook and would like it to work.

If anyone wants to see any of my config files, please let me know which ones.

---

### Post by thomasaaron on 2010-03-10
Hmmm... Same thing I have. OK, thank you.

I'll just re-image this shop unit and try again.

---

### Post by thomasaaron on 2010-03-10
For anyone tuning into this topic...

Installing pavucontrol, re-installing ALSA and that sort of thing should NOT be required, and doesn't seem to help. Once you start doing that, you reduce the chances that we will be able to help you without a fresh install.

Your microphone works out of the box on the Starling (tested with Sound recorder). The problem here is not your mic, but issues between Skype and pulseaudio.

Skype has not continued to keep pace with Ubuntu. Their latest release is for Ubuntu 8.10.

Skype worked fine in 9.04 on the Starling.

Some folks have it working well out of the box with 9.10 and the latest version of Skype. But I believe that as Ubuntu progresses, and Skype does not, Skype support is going to drop WAY off.

For now, I'm running some more tests on our shop Starling to try and figure out a good solution.

---

### Post by PatrickVogeli on 2010-03-11
tom, could you try launching skype using this order:

/bin/sh -c "PULSE_SERVER=127.0.0.1 /usr/bin/skype"

This should make skype work using good ol' alsa.. maybe running it that way and playing a bit with alsamixer could be the way to go.

My laptop also had pulseaudio - skype problems and that fixed it..

---

### Post by riseringseeker on 2010-03-12
> **thomasaaron said:**
> For anyone tuning into this topic...

Installing pavucontrol, re-installing ALSA and that sort of thing should NOT be required, and doesn't seem to help. 

Tom, do I have a wrong impression of what pavucontrol is?  I thought it merely the controls for PA, which is of course already the default scheme.

---

### Post by ants280 on 2010-03-12
> **PatrickVogeli said:**
> tom, could you try launching skype using this order:

/bin/sh -c "PULSE_SERVER=127.0.0.1 /usr/bin/skype"

This should make skype work using good ol' alsa.. maybe running it that way and playing a bit with alsamixer could be the way to go.

My laptop also had pulseaudio - skype problems and that fixed it..

WOOHOO!  Thanks a million!  That fixed my Skype woes!!!  +rep

---

### Post by thomasaaron on 2010-03-12
Ants280,

Yep, thanks another million. That did it. I guarantee you THAT is going in my bag-o-tricks.

I appreciate the pointer.

---

### Post by macynelliot on 2010-03-19
Having the same problem.  None of the mentioned fixes works for me.  Any other suggestions?

---

### Post by thomasaaron on 2010-03-19
macynelliot,

Do you have a Starling?
What version of UNR are you running? 9.04 or 9.10?
What version of Skype are you running?
Do you have your mic working with Sound Recorder?
Have you downloaded any packages pertaining to pulseaudio in your attempt to get it working?

---

### Post by tlroche on 2010-10-14
I tried to setup skype on my panp5 and on my GF's star1 just now, both running vanilla GNOME lucid, both fully up-to-date. I was able to test-call OOTB on the panp5, but on the star1, test call failed--no playback volume on my voice. I also noticed that

```
arecord -f cd /tmp/junk.wav
# I speak a bit, then hit C-c
totem /tmp/junk.wav &

```

played back my voice, but with very loud background noise, as if the mic was overdriven. More research found ants280's post above, i.e.

> **PatrickVogeli said:**
> 
```
/bin/sh -c "PULSE_SERVER=127.0.0.1 /usr/bin/skype"
```


which also fixed the star1's problem, after I made the skype icon run the line of code above. HTH.

---

### Post by jerickson314 on 2010-12-29
Just an FYI - the 
/bin/sh -c "PULSE_SERVER=127.0.0.1 /usr/bin/skype

fix works on my star1 on 10.04.1 with the Partner Repository version of Skype (2.1.0.81 Beta).  It's still broken in 10.04.1 otherwise.

Thanks!

---

