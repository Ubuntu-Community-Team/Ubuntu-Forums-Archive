---
title: "Mic/Line In not in &quot;Recording&quot; section of Volume app"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by jem7v on 2008-06-15
I'm not quite sure if this is the right section to post under or not, but oh well... if it's wrong, I'm sure somebody will tell me.

I can't record from my line-in or my microphone.  Quite simply, the system knows that they're there and it lets me set the playback level for them (and thus I know that they work), but it doesn't let me record from them.

Just like the title of the thread says, Microphone and Line In level controls both **exist under the Playback tab** in the Volume controls, but they **don't exist in the Recording tab** (which suggests they can't be recorded from?).  Instead all I have are "Capture" and "Digital."  I've gone into Volume Control's preferences and ticked off every single option, so I know they aren't just hiding on me.  The help file for the Volume app is 4 years old, so it's totally useless.  Does anybody know what "Capture" and "Digital" are supposed to record?  Does anybody know how I could get Mic and Line In to show up there?  Any suggestions?

I've tried all sorts of methods to record with Sound Recorder and Audacity, and I'm just not even sure where to go from here.  There are so many different sound systems listed (various ALSA things, OCC, PulseAudio, etc) that I don't even know what I'm supposed to use any more or what the difference is going to be between them. My last PC was running 7.10 and I didn't have issues recording, but this one has a different sound card and I have no idea how to get it to record.

Currently running Ubuntu 8.04, plain old on-board sound.  I think it's an NVidia chipset, but I'm not sure about that.
I've also tried recording through a borrowed M-Audio MobilePre USB, and although Ubuntu recognizes it when I plug it in and powers it, I can't figure out how to get Ubuntu to actually listen to the sound from it, so it's currently useless too.  Sigh.

---

### Post by paulg on 2008-07-07
See [here]("http://ubuntuforums.org/showthread.php?t=846621") for instructions on getting the MobilePre operational in Hardy. Since you have it available to you, you should find that the recordings on the MobilePre are a little better thanks to the added control with the built-in preamps which will allow you to get the best levels out of your instruments (mic or instrument patch).

To get more than two channels recorded at the same time you will need a dedicated card that will allow multiple recordings. With the MobilePre you can record up to two channels at a time but with a multichannel recording program, such as ardour, you can record as many additional tracks as you want, while playing back previously recorded tracks in realtime (there's probably a technical limit but you'll probably hit your system's limit to keep up first). Look on this forum for information on ubuntu-studio. You can add the packages from the main Ubuntu repositories. Ardour, JACK (qjackctrl) and linux-rt (realtime kernel) are the programs and kernel that you should look into to get started.

---

