---
title: "JACK/Qsynth/Rosegarden - Output to Soundcard"
date: 2012-12-07
forum: Ubuntu Studio
---

### Post by vidwarren on 2012-12-07
Hi,

I'm running Rosegarden to play a MIDI soundfont (using and electronic drum kit to trigger the notes). I'm using QJackCtrl and Qsynth.

I can trigger the notes and get sound from my laptop.

The problem I'm having is that I can't output the sound through my USB-soundcard (Alesis iO|2 audio/MIDI interface). It's the same interface that the MIDI is coming through.

Sound works fine coming solely out of the interface when I play a .wav in audacity. So it's just a case of switching a connection around I'm sure.

I tried both setting the interface to hw:1 (labelled as iO|2) and to hw:1,0 (labelled as USB Audio - which is what is listed in Audacity) in QJackCtrl's Setup. It still plays from the laptop...and yes, I did restart QJackCtrl.

Under QJackCtrl's Connections window, iO|2 doesn't appear to be listed under 'Audio'. It is listed under ALSA but is unconnected on both the input and output side. I've tried connecting it there but it just cuts the sound out entirely.

I can't seem to find any relevant audio output settings in Rosegarden. I assume that they wouldn't be there because it doesn't make sound on its own anyway?

Really, I don't know where to look. Any ideas?

Thanks in advance,

Vid


EDIT: I've just discovered that I still get sound (through the laptop speakers) even when QJackCtrl isn't running. This suggests to me that my QJackCtrl settings are not having an effect anyway. Is that right? How can I connect Qsynth/Rosegarden to QJackCtrl?

Or, how can I modify the settings without using QJackCtrl?


EDIT #2:

I tried installing Patchage to connect there. The iO2 soundcard comes up as 4 (green) ALSA based MIDI channels - In, out, Through and another Through. Nothing is (red) Jack controlled MIDI. The only (blue) audio connections are qsynth, system playback and system record.

What I think is happening is the connection is automatically being made via ALSA to *the first available audio output*. Which is my laptop's HDA internal soundcard.

I can't find anywhere to select the iO2 - except for QJackCtrl, which doesn't seem to be connecting. Is there a way to change priority for ALSA? Would that be the best way to do it?

---

### Post by vidwarren on 2013-01-27
Still haven't had any luck. Does anybody here use a USB soundcard to import MIDI and export audio simultaneously?

---

### Post by Adan1900 on 2013-02-26
Hi, had the same problem and found a solution.
**It is qjackctl** that uses it's default sound output. You want to find out the number of the desired sound card, by runing in terminal **cat /proc/asound/cards**
Then, in **qjackctl**, press the **Setup button**, (under Settings submenu) on the right column, you can change the "interface" with the desired sound card, but I believe that also changes the microphone input to that sound card. To change only the output, go to **Output device, **and **replace (default) with hw:1** (or hw:2 ; it is the number corresponding to your desired sound card) then restart qjackctl

found the solution at
[http://docs.fedoraproject.org/en-US/Fedora/15/html/Musicians_Guide/sect-Musicians_Guide-Using_JACK.html](http://docs.fedoraproject.org/en-US/Fedora/15/html/Musicians_Guide/sect-Musicians_Guide-Using_JACK.html)

---

### Post by rmorrisppc on 2013-03-17
I am in a similar boat - I am a complete newb to ubuntu/linux.  I have been able to load 10.4 thru 13 on my little G4 powerbook ppc.  However, the one that seems to run the best is 10.4
Now I am trying to use Rosegarden and kinfocenter is telling me that the midi and synth devices are not enabled.  All I would like is to load some midi files into rosegarden to be able to aid as a music practice tool (like playing with a whole band) but I cannot get it to make sound.  I am about to just go out and drop money into a new intel laptop and just walk lockstep with the herd so I would have something that works.
Please help - and remember - complete newb.  Thank you

---

