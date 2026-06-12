---
title: "Ubuntu 9.10, problems during recording and playback"
date: 2009-11-05
forum: Ubuntu Studio
---

### Post by aeh on 2009-11-05
Hi

I have just installed 9.10 with everything. I have attempted to record audio with Ardour. I use JACK which seems to run normally. My soundcard is a M-Audio Fast Track Pro USB. I have been able to record sounds with a mic attached to the no 1 input of the FasttrackPro. I can, however, not play it back with the same settings as recording, as I must change the settings in JACK setup. Then I can get playback, but no recording. I) have absolutely no idea how to set it up and how to connect things in JACK. I am also unable to open Envy24control. Are these problems because of Pulse? Please help!!
Rgds
Alex

---

### Post by trulan on 2009-11-05
No, the problems are not because of Pulse.  Jack suspends Pulse as soon as you start it, so if Jack is running at all Pulse is not (unless you modified it in an attempt to make Jack and Pulse work at the same time.)

Would you mind posting a screenshot of your settings in Jack?  That would be helpful.

Also, how familiar are you with making connections in Jack?  Have you used the connections settings in Ardour's mixer, or in Jack Control's patchbay, or in Patchage?

It sounds like you are pretty close to getting things to work.

---

### Post by aeh on 2009-11-06
Hi Trulan
Here are some screenshots. No I am not familiar with making connections, there are no instructions whatsoever. I have looked at JACK's connections and patchage but I have no idea how to use them. In Ardour's mixer I tried to fiddle back and forth with the outputs, it looks like there is sound coming out, the meters do move, but there is no sound. I have not tried Jack Control's patchbay, I have no idea how to use it. I've had a look at Patchage. 
No matter how I connected the input and output devices (see screenshot rec_no_playback) it seemed that I could always record, even when JACK wasn't running! However, I haven't been able to find out which input/output combination allows playback.
Please see other attached screenshots. (BTW some time ago I connected said Fast Track Pro to my laptop with Vista and Magix Audio Studio 2004, no problems)
A

---

### Post by aeh on 2009-11-06
See above. I have been able to visually confirm simultaneous rec + playback, but no sound.

---

### Post by AutoStatic on 2009-11-06
Hello eah, looks good. But you are now using the same hardware ID for both recording and playback. It should be possible to select different ID's if you click on the **>** next to Input Device and Output Device. It should give you the option to select hw1,0 for recording and hw1,1 for playback. I could be wrong, I don't own a FasttrackPro and I always set the interface on hw1 (or any other ID the device has) and use Duplex. You could also try playing around with the in- and output channels.

---

### Post by aeh on 2009-11-06
I tried to use Patchage, it seems that it starts with capture, then it goes to something in. From something out it goes to playback. But shouldn't these somethings be connected?

---

### Post by aeh on 2009-11-06
It seems I can record and playback with Audacity: recording - pulse, playback - hw 1   Fast track pro

but not with ardour. There is a connection problem somewhere. Any help appreciated

---

### Post by AutoStatic on 2009-11-06
I'm sorry, I was talking mumbojumbo about the hardware ID's. But did you already play around with the input and output channels?

---

### Post by aeh on 2009-11-07
> **AutoStatic said:**
> I'm sorry, I was talking mumbojumbo about the hardware ID's. But did you already play around with the input and output channels?
In JACK or in Ardour? I wish I knew what all those inputs and outputs and whatnot means....   ;) I wish there was a tutorial or something

---

### Post by AutoStatic on 2009-11-07
JACK. Unfortunately there's no good English manual for Qjackctl or JACK. There's [a good Dutch one]("http://wiki.linuxmusicians.com/lib/exe/fetch.php?id=manuals_tutorials_and_howto_s&cache=cache&media=qjackctl_handleiding4.3_nl.pdf") though but your Dutch is probably abominably bad :D

---

### Post by trulan on 2009-11-07
Per your screenshot of Patchage:
* **System Capture** - that's your mic or line input.  It's stereo, that's why there are two system captures, one for left and one for right.  As you can see, you have System Capture 1 connected to the input of four tracks in Ardour
* **The Ardour box** - shows all the internal connections Ardour makes.  You have four tracks in your project, named Audio 1, 2, etc.  They are mono tracks, so there is only one input per track.  The sound flows down vertically through that track's channel in Ardour's mixer window, being affected or controlled by each item in succession.  
   Notice that each track has two outputs.  Those outputs are stereo, with each number one being connected to Master In 1 and each number two being connected to Master In 2.  The Master channel is a bus (like a track, ecxept it gets its inputs from the other tracks in the project.)  Again, the sound flows down through the channel (in the mixer), starting at the top and coming out at the bottom.  It leaves the Ardour box as Master/out one and Master/out 2.
* **System Playback** - this is your soundcard.  Again, it is stereo, so there are two outputs.  Anything connected to this should put sound out your speakers.

If you connect system capture directly to system playback, you should get sound directly from your microphone to your speakers.

The only thing different from normal in your shot of the patchage window is that you have the outputs of Audio 1 connected directly to system playback - that should be disconnected as they are already being routed through the Master bus to system playback.

I realize this may not actually get things working for you.  But you asked for an explanation of JACK connections and there you have it.  Hope it made sense.

---

### Post by aeh on 2009-11-07
> **AutoStatic said:**
> JACK. Unfortunately there's no good English manual for Qjackctl or JACK. There's [a good Dutch one]("http://wiki.linuxmusicians.com/lib/exe/fetch.php?id=manuals_tutorials_and_howto_s&cache=cache&media=qjackctl_handleiding4.3_nl.pdf") though but your Dutch is probably abominably bad :D
Probably no worse than your swedish or finnish  :D

---

### Post by aeh on 2009-11-08
My mobo (Asrock P4i65GV) has a built in soundcard AC97. Should it be enabled or disabled? Needless to say I still haven't had any success...

---

### Post by aeh on 2009-11-08
Ah, got it working, it was all about JACK connections     :)

---

### Post by aeh on 2009-11-09
And thanks for the help!

---

