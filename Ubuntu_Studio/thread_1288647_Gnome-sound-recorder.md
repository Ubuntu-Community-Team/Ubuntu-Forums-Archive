---
title: "Gnome-sound-recorder"
date: 2009-10-11
forum: Ubuntu Studio
---

### Post by cpeachey on 2009-10-11
I am trying to record my LP's from a turntable, via a USB sound card.
Audacity does not want to know!
Gnome-sound-recorder records the tracks but SILENTLY! When I play the back the track I get the sound.
I get the same result if I use an existing sound file. (no sound whilst recording, ok on playback.)
Any ideas please?
Is the sound muted? There are crosses against the speakers, when clicked the text greys out, unclick and it goes bold but the crosses remain.
Chris

---

### Post by Junkieman on 2009-10-11
Hi

Suggest checking your levels, on the main toolbar right-click the speaker (that controls your main volume) and click Open Volume Control. Go through the Devices dropdown, and on the Recording tab check that your input levels are not too low (or muted). 

Also in Audacity in the preferences (Ctrl+P) make sure the right recording device is chosen.

---

### Post by cpeachey on 2009-10-11
I have checked all the sliders. and the input card for Audacity. (Audacity works with the new 9.10 version but same no soud whilst recording.
Pulse Audio Volume Control has a red cross against all the speakers, see above. 
Volume control Capture window shows red cross on and off as toggled. Is there a master "Mute" somewhere?
Chris

---

### Post by Junkieman on 2009-10-11
The fact that Gnome-sound-recorder does record (though too soft) shows that the hardware is working. I haven't ever seen a master mute control before, only the options in the Volume Control.

Have you tried other recording devices in Audacity? I don't use Pulse audio, but OSS or ALSA.

---

### Post by cpeachey on 2009-10-11
Not quite sure what is meant here...
"Have you tried other recording devices in Audacity? I don't use Pulse audio, but OSS or ALSA?"
Are these other software programs?
Chris

---

### Post by Junkieman on 2009-10-11
> **cpeachey said:**
> Not quite sure what is meant here...
"Have you tried other recording devices in Audacity? I don't use Pulse audio, but OSS or ALSA?"

In Audacity preferences on the "Audio I/O" page, you can specify the Device to record from, mine lists "OSS" and "ALSA: HDA Intel". Which one is yours set at? Try switching between these...

---

### Post by cpeachey on 2009-10-11
ALSA pulse is the only option.
In Recording there is a long list which includes my internal sound card (correct) and also the USB card which is what I want to record from but is not shown in the recording choices.
Chris

---

### Post by Junkieman on 2009-10-11
Thats strange that you only have the one option. OSS was installed by default on my system, I'm using Intrepid 8.10, which release are you running?

You can try installing the oss driver

```
sudo apt-get install alsa-oss
```

Just take note if it says that it's already installed if you run this command.

I'm not quite sure what else to suggest at this point, does anyone else have something we can try?

---

### Post by cpeachey on 2009-10-11
I have just re-installed Audacity and now get several choices.
ALSA NVidia Analog etc
ALSA USB Audio CODEC etc
ALSA pulse
ALSA default
OSS DEV/dsp
OSS dev/dsp1
Chris
I have tried all the above as imputs
OSS gives the message...
Playback and Recording device must use the same type, i.e., MME, DirectSound, etc.
ALSA NVidia shows some activity, a straight recording line that stops after 6 seconds (no signal?)This also shows a drop down list of imputs. ( I am not imputting via this card)
ALSA USB does not show any recording activity. (I think it should)
ALSA Pulse and Default do not show any activity.
So it looks as though it is not getting the signal from the USB sound card even though it does list the USB card.
Note that I am using 9.04
I did try 9.10. This DOES record as above but does it silently!
If I could only hear something whilst recording this would be a major breakthrough.!
Thankyou for your help and patience. Any other thoughts please from anyone?
Chris

ps If I set record and playback to USB I get recording activity for 18 seconds then it stops. Is it trying to monitor the sound through the wrong output? And why stop after 18seconds. (The LP record is still playing)
Chris

---

### Post by Junkieman on 2009-10-11
Change between the options, one at a time, and see if recording gets any audio. Some of these might give the message "Error opening sound device", if so move on to the next option. Also close any music/media players that might take up the sound card.

To get details about your sound hardware you can also use
```
sudo lshw -c multimedia
```

---

### Post by cpeachey on 2009-10-12
I think the problem is Ubuntu does not like my USB sound card even though it reposts it's existance.
Windows/Audacity records ok with sound via the PC's on-board sound card.
(I am using Ubuntu almost exclusively now)
Whilst Audacity/Ubuntu does not record at all with the same settings.
I'll give it a rest now and try again in a few days.
Thanks for the help.
Chris

---

### Post by Junkieman on 2009-10-12
Sorry we couldn't get it recording. You're probably right about it being USB, why it's being quirky. Search for your card model, there must be other users who had the same issue before.

---

### Post by cpeachey on 2009-10-26
I have now changed my pre-amp to one that connects to the motherboard line-in. Sound now OK! Recording starts then stops after 12 seconds then almost immediately. Now looking at what causes this.
Chris

edit
I have unchecked Software Playthrough (both boxes) and recording is now OK
Greeeeeeeeeeeeeeeaaaaaaaaat!!!!!!!!!!
Chris

---

### Post by Junkieman on 2009-10-28
Great job! I didn't even think of software play-through, it's off by default. Thanks for posting the solution, happy recording :)

---

