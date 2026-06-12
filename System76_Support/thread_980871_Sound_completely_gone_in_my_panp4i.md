---
title: "Sound completely gone in my panp4i"
date: 2008-11-13
forum: System76 Support
---

### Post by phyzome on 2008-11-13
Yesterday evening I noticed that I could not get my Pangolin Performance to produce any sound whatsoever. I tried rebooting and killing pulseaudio (which usually does the trick), but no luck. I even tried cat'ing a random file to /dev/audio (I believe that bypasses most or all of the software layers), but I got nothing.

The sound card isn't (completely) dead, because I hear a little electric click through the headphones when I plug/unplug them.

I haven't screwed around with sound configuration in the past week or so, and no sound-related packages have been updated, installed, or removed.

I also haven't heard the system make this "deedle deedle deedle" noise that it usually makes after waking up from an overnight suspend or hibernate. (But that's a question for another thread...)

So, is my sound card screwed up, or just one of the software layers? What can I do to determine this?

---

### Post by jpoRS on 2008-11-13
I had a similar problem, and to fix it I had to go to the Volume Control menu, and in preferences enable all of the options.  Turns out one of the channels was muted.

Don't ask me how it got muted, but there we are.

Good luck,
jim

---

### Post by phyzome on 2008-11-13
> **jpoRS said:**
> I had a similar problem, and to fix it I had to go to the Volume Control menu, and in preferences enable all of the options.  Turns out one of the channels was muted.

I already checked that, including the other Devices in the File menu.

I also poked at [Fn]+[F3] (mute/unmute) to ensure that wasn't the problem.

---

### Post by Derath on 2008-11-13
I'm having the same problem, I was wondering if it was related to the kernel modules update a few days ago...
panp4n
KDE 3.5
Ubuntu 8.04

---

### Post by thomasaaron on 2008-11-13
> So, is my sound card screwed up, or just one of the software layers? What can I do to determine this?

Boot from a live CD and see if you have sound.

I'm imaging a PanP4 and updating it to see if anything hosed sound.

---

### Post by phyzome on 2008-11-13
> **thomasaaron said:**
> Boot from a live CD and see if you have sound.
Sound worked when I booted from LiveCD. (I suppose that's the good news *and* the bad news.)

Good tip, though.

---

### Post by thomasaaron on 2008-11-14
Do you have skype or some other program auto-starting when you log in.
If it is using the sound card, it might be blocking other apps from using it.

I know this was an earlier bug with pulseaudio. I'm not really clear, though, on whether or not it's been fixed.

---

### Post by phyzome on 2008-11-14
> **thomasaaron said:**
> Do you have skype or some other program auto-starting when you log in.

Nope. I also use FlashBlock in Firefox to prevent that from stealing the soundcard, which it is prone to do.

---

### Post by thomasaaron on 2008-11-17
If you've got the pull-downs in System > Prefs > Sound set to Pulse Audio,
and you don't have the PCM, MASTER, or FRONT sliders turned down too far or muted, I'm not really sure.

It could be that some configuration is hosed, or perhaps something you have downloaded has broken ALSA.

Since it works from a live CD, my first line of attack would be checking to make sure you don't have something set wrong in your sound control panel. Take some screenshots of your settings on each tab, and we can have a look at those.

Second, what sound-using programs have you downloaded prior to the problem?

---

### Post by phyzome on 2008-11-17
> **thomasaaron said:**
> If you've got the pull-downs in System > Prefs > Sound set to Pulse Audio,
and you don't have the PCM, MASTER, or FRONT sliders turned down too far or muted, I'm not really sure.

Check, check, all check.

> **thomasaaron said:**
> It could be that some configuration is hosed, or perhaps something you have downloaded has broken ALSA.

Since it works from a live CD, my first line of attack would be checking to make sure you don't have something set wrong in your sound control panel. Take some screenshots of your settings on each tab, and we can have a look at those.

Attached.

> **thomasaaron said:**
> Second, what sound-using programs have you downloaded prior to the problem?

Nothing, as far as I can tell. I recently upgraded Pidgin, but I think that was after the problem started.

Are there any conf files I can post?

---

### Post by phyzome on 2008-11-18
It must have been a hosed config file -- I upgraded to Intrepid, and the problem has disappeared.

I recall seeing an ALSA config file being replaced during the upgrade, so that was probably it.

---

### Post by Derath on 2008-11-18
Okay, I guess I need to bite the bullet and upgrade myself... or would reinstalling alsa work?

---

### Post by thomasaaron on 2008-11-18
Derath,

What is your System76 model number? Do you have the PanP4i?
Also, did you check your sound with a live CD?

Best,
Tom

---

### Post by phyzome on 2008-11-18
Dareth, the upgrade also solved another sound issue I had, which was an interaction between Flash, PulseAudio, and suspend.

---

### Post by thomasaaron on 2008-11-18
Phyzome,

I heard that Adobe FINALLY released a 64-bit flash plugin. I believe Ubuntu ill be putting it in the repos soon. Still researching it.

---

### Post by Derath on 2008-11-19
updated to 8.10, I have sound back, and now I have to learn kde4

---

### Post by Brickrat on 2008-11-22
I have a month old Pangolin and everything has been working fine, except the sound has quit working.  I have checked the above items and system>preferences>sound looks ok, although mine were set to autodetect instead of pulse audio, I changed them, and pushed the test button but still no sound. 

The first time I went into the sound the headphone box was check so I unchecked it and tried the tests again, still no sound. 

I reinstalled the system76 drivers, still no sound. 

I have been running Pidgin so I checked that and the mute sounds was checked in it so I unchecked that, but still not sounds. 

Sure would like some help.  I really don't like having to fix my computer every weekend, I'd rather use it. 

(I've invest about 40 hours trying to get the wireless working on my daughters ACER with Ubuntu 8.04 and Atheros AR5007 wireless card, but that's a whole other deal.)

---

### Post by Brickrat on 2008-11-23
OK so I went into Synaptic and marked the installed ALSA packages for reinstallation and after rebooting the sound was back.  So I guess my problem is fixed, at least for now, since I really don't know what happened.

---

### Post by psyke83 on 2008-11-24
> **phyzome said:**
> Yesterday evening I noticed that I could not get my Pangolin Performance to produce any sound whatsoever. I tried rebooting and killing pulseaudio (which usually does the trick), but no luck. I even tried cat'ing a random file to /dev/audio (I believe that bypasses most or all of the software layers), but I got nothing.

The sound card isn't (completely) dead, because I hear a little electric click through the headphones when I plug/unplug them.

I haven't screwed around with sound configuration in the past week or so, and no sound-related packages have been updated, installed, or removed.

I also haven't heard the system make this "deedle deedle deedle" noise that it usually makes after waking up from an overnight suspend or hibernate. (But that's a question for another thread...)

So, is my sound card screwed up, or just one of the software layers? What can I do to determine this?

Intrepid has a bug where the PCM mixer gets muted - you should check it.

I recommend you follow [this]("http://ubuntuforums.org/showthread.php?t=789578") guide. See Part C, Step 3 to ensure your PCM mixer is not muted.

---

### Post by thomasaaron on 2008-11-24
...as an addendum to that excellent information... here is a quick, preliminary check that gets a lot of people up and running on System76 machines...

First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, go to Edit > Preferences. (If you are using Ubuntu 8.10, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to ALSA. (If you are using Ubuntu 8.10, make sure all of them are set to Pulse Audio instead.) Click the first Test button to see if you now have sound.

---

### Post by OldDirtyTurtle on 2008-11-24
Once again...

Thanks Tom!

See folks - that's why I love Ubuntu and System76.  Got a problem, log on, ask or read, follow advice, problem solved.

:guitar:

---

### Post by thomasaaron on 2008-11-24
Thanks. (You just haven't seen me royally screw it up yet!) :lolflag:

---

