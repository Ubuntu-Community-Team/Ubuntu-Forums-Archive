---
title: "Ardour: Horrible Cracks but only when recording, or playing back"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by secondstage on 2008-07-07
When I am just playing without Ardour or Jack, there is a clean, crisp sound, but when I playback a recording, it cracks alot. Also, I'm getting Xruns, when there is nothing playing, could this be my problem? The first attachment will be a screenshot of Alsa Mixer, Jack running (with the settings shown), and Patchage with Ardour open. 

Any ideas would be greatly appreciated.

--secondstage

---

### Post by secondstage on 2008-07-07
Attachment

---

### Post by Stochastic on 2008-07-07
do you have the linux-rt installed? if you're not sure, run ```
uname -r
``` and post the results.

It sounds like XRUNS are your issue (they sound like cracks/pops/glitches) but you've got a pretty high frames/period already, maybe try changing your period/buffer to 3.  My personal setup doesn't have "Unlock Memory" or "Monitor" checked, so you might want to try unchecking those to see if it changes anything.

---

### Post by secondstage on 2008-07-07
I do have to Realtime kernel. I unchecked Unlock Memory, and Monitor, but they don't seem to have any effect. There was an outrageous buzz without Ardour, or Jack, but that was a faulty cable. Now I bend the cable so it doesn't buzz. The cable still works, and it's my only option right now (I'll try to borrow one until I go to the store). Changing Period/Buffer got rid of the XRUNS, but there's a new problem, Ardour doesn't pickup any sound. Nothing, not even on that VU Meter bridge thing. Everything is connected the some way as before. It can't a problem externally, because I changed the input from a keyboard to a Microphone and back again, and still no success.

Thanks so far,
--secondstage

PS I'll be out of town for 1-2 days, so if you don't hear back, don't assume I quit and gave up (I just won't be able to do anything to this computer).

---

### Post by thorgal on 2008-07-08
intel-HDA : set the periods/buffer to 3 in the jack setup window. According to your screenshot, it is set to 2. There are also some module options that may help. I don't remember them because I don't use this chipset (disabled it the BIOS). If you type this in a terminal:

sudo modinfo snd-intel-hda

you will see a list of parameters. IIRC, one of them corrects a timing error, the parameter is called position_fix or something like that. BUt maybe this has been already fixed. Try the n = 3 setting in qjackctl and you should see fewer xruns.

---

### Post by vvoois on 2008-07-09
If you have any windowmanager like Combiz or Beryl installed, i would suggest you to disable these as they consume a hell of a lot of cpu resources and cause confusing xruns in Jack.
At least the RealTime kernel does not allow Jack and Combiz to be friends together.
And as Ubuntu 8.04 comes with Combiz enabled by default, chances are likely you may have this enabled (if you have Ubuntu 8.04)

I have got results from a colleague who disabled Compbiz and could change  the Frames/period back from 512 to 128. (512 f/p was the lowest he could go with the least xruns)

---

### Post by secondstage on 2008-07-09
I do use 8.04 (hint: avatar). Compiz doesn't take much my resources(maybe 30% when rotating the 6-sided cube using mouse, with dome, 3d windows, awn, animated gifs, and a system monitor), but I'll try what you said anyway. I have to get used to not having 6 desktops, and AWN. :(

---

### Post by thorgal on 2008-07-09
dude, try what I said in the before previous post. Your jack setting is wrong.

---

### Post by secondstage on 2008-07-09
@Thorgal: Will do. I just reinstalled to remove any other problems, but I still have those runs. I'll post my results in minute or two.

**EDIT:** When Periods/Buffer (P/B) was at 3, and Frames/Period (F/P) was at 1024, JACK wouldn't start (exit status=256). I dropped F/P to 512, and kept P/B at 3, and JACK started fine. Here is what the Messages box had to say after the drop:
> 15:14:13.863 Patchbay deactivated.
15:14:13.921 Statistics reset.
15:14:13.928 Startup script...
15:14:13.928 artsshell -q terminate
15:14:13.956 ALSA connection graph change.
15:14:14.346 Startup script terminated with exit status=256.
15:14:14.346 JACK is starting...
15:14:14.347 /usr/bin/jackd -R -m -dalsa -r44100 -p512 -n3 -D -Chw:0 -Phw:0 -m
15:14:14.349 JACK was started with PID=6034.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|512|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 3 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
15:14:14.549 ALSA connection change.
15:14:16.554 Server configuration saved to "/home/john/.jackdrc".
15:14:16.555 Statistics reset.
15:14:16.556 Client activated.
15:14:16.558 JACK connection change.
15:14:16.560 JACK connection graph change.

NOTE: I think the first 15:14:14.346 exit status thing is from the first startup. 

What can I do for...> JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory?

---

### Post by Stochastic on 2008-07-09
Have you edited any settings in the Ubuntu Studio Controls?  they can be found under System -> Administration -> Ubuntu Studio Controls

You may want to enable memory lock, and turn it up to about 95% range.

---

### Post by secondstage on 2008-07-11
> Have you edited any settings in the Ubuntu Studio Controls? they can be found under System -> Administration -> Ubuntu Studio Controls

You may want to enable memory lock, and turn it up to about 95% range.

Tried it, but Jack still has problems with allocating the memory.

---

