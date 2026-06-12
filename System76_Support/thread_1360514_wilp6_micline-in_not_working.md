---
title: "wilp6: mic/line-in not working"
date: 2009-12-21
forum: System76 Support
---

### Post by dabrowsa on 2009-12-21
I've got a 64-bit wilp6 running Ubuntu 9.10.  Sound out works fine but I can't get sound in working.

I've got a cable from a synth plugged into the green jack in back.  I've tried fiddling with sound preferences, the mixer, gstreamer-properties, system76 driver installer (all drivers provided by Ubuntu).

I'm stumped.

---

### Post by riseringseeker on 2009-12-21
> **dabrowsa said:**
> I've got a 64-bit wilp6 running Ubuntu 9.10.  Sound out works fine but I can't get sound in working.

I've got a cable from a synth plugged into the green jack in back.  I've tried fiddling with sound preferences, the mixer, gstreamer-properties, system76 driver installer (all drivers provided by Ubuntu).

I'm stumped.

I have a Wild Dog as well.  Try plugging the microphone into the "pink" input jack - where it is on mine, and works fine.

---

### Post by dabrowsa on 2009-12-21
Tried that, didn't seem to help.  Anyway, shouldn't the green jack be the correct one for output from a synth?

---

### Post by thomasaaron on 2009-12-21
Please see the attached screenshots. They may help. (They are provided courtesy of riseringseeker.)

---

### Post by dabrowsa on 2009-12-21
Those screenshots might be very helpful if I knew what control panel was shown in them.  It's not gnome-volume-control or any of the others I mentioned above.

---

### Post by riseringseeker on 2009-12-21
> **dabrowsa said:**
> Those screenshots might be very helpful if I knew what control panel was shown in them.  It's not gnome-volume-control or any of the others I mentioned above.

Why the pulse audio controls are not included with the base install I don't know, but open and terminal and paste the below in to it and press enter.

```
sudo apt-get update && sudo apt-get install padevchooser 
```

Then you will have the same control panels.  

I had troubles with my Wild Dog as far as audio output when I installed Karmic.  I had it set as "color-coordinated" as to jacks and input.  That worked fine until Karmic.  Turns out that I had to move the speakers to another jack, I posted here when I found out about it.  

Do you have a USB mike to play with, even one you can borrow?  If it works with a USB mike, then it's not a hardware problem, but one of configuration.   As you can see from the screenshots that Tom posted, I have a total of 3 microphones (and they all work) on my Dog.

---

### Post by dabrowsa on 2009-12-21
Progress!  The command for the Volume Control window is pavucontrol.  Launching that I can now see that the red mic jack in the rear is working (the meter registers the output from the synth), although the blue line-in jack does not seem to.  I think Mic1 had been muted in the pavucontrol input devices pane.  Maybe the problem with line-in is similar, but the only ports available under Internal Audio Ananlog Stereo are the mics.  So for now at least I'll forget about the line-in.

The present problem is that although the input meter is dancing and I can record with SoundRecorder, I can't hear the signal during the input.  Is there some playthru setting somewhere that can click to pipe the mic input directly to speaker/headphone output?

---

### Post by dabrowsa on 2009-12-21
OK, I've got the mic playthru working.  The solution is at:

[http://ubuntuforums.org/showpost.php?p=8308073&postcount=3](http://ubuntuforums.org/showpost.php?p=8308073&postcount=3)

I still don't understand why the line-in jack isn't working or even acknowledged by pulse though.

---

### Post by dabrowsa on 2009-12-21
Regarding the line-in problem, perhaps it's an issue with alsa rather than pulse, because "line" doesn't appear on the capture page of alsamixer: only Front Mic, Mic, Capture, Capture, Input Source, Input Source.  

Also, on the Playback page, Front Mic Jack and Mic Jack have no slider control, just a toggle for line-in/mic.  Toggling makes no difference that I've been able to tell.

---

### Post by riseringseeker on 2009-12-24
> **dabrowsa said:**
> OK, I've got the mic playthru working.  The solution is at:

[http://ubuntuforums.org/showpost.php?p=8308073&postcount=3](http://ubuntuforums.org/showpost.php?p=8308073&postcount=3)

I still don't understand why the line-in jack isn't working or even acknowledged by pulse though.

Line-in shows here - see screenshot.

---

### Post by dabrowsa on 2009-12-24
It doesn't show on mine.  All I see in the corresponding pop-up menu are "Microphone 1" and "Microphone 2".  So is it some Alsa module that needs to be loaded?  I haven't a clue.

---

### Post by riseringseeker on 2009-12-25
> **dabrowsa said:**
> It doesn't show on mine.  All I see in the corresponding pop-up menu are "Microphone 1" and "Microphone 2".  So is it some Alsa module that needs to be loaded?  I haven't a clue.

I haven't added anything in the way of sound stuff, other than the padevcontrol and the like - well, exaile, audacity, etc., but nothing that relates to the overall sound system itself.  If ALSA, or any module is installed it was by default.

---

### Post by dabrowsa on 2009-12-25
Maybe it has something to do with my not running Gnome?  I use xfce4.  I wouldn't think that would matter but is a difference between your setup and mine.  When I get a chance I'll see if anything is different under gnome.

---

