---
title: "LMMS recognize Midi keyboard"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by Affrikka on 2010-01-10
Hey everyone

(sorry for making so many topics in such little time, I really want to get this working and I have lots of questions :P)

I have my digital piano plugged into ubuntu 9.10 through a USB, and I know its working because I can use it for input into MuseScore.

I recently downloaded LMMS and I want to know how to tell LMMS to use my midi keyboard, I cant find it anywhere (although I can't ever find anything anyway :P)
how do I do that?


thanks!



Mathieu

---

### Post by Affrikka on 2010-01-10
bump

---

### Post by AutoStatic on 2010-01-11
In your Beat+Baseline Editor click on the Tools icon on the left, select MIDI - Input - Your MIDI controller

---

### Post by Affrikka on 2010-01-11
hey,

I have the Beat+Baseline Editor, I clicked on the little Wrench and Screwdriver and went down to MIDI and clicked input but all it does it put a check by input and nothing else....
Is there a menu on here that shows that if I hit a key on my piano it will show that its getting feedback?

i wonder if it would also make a difference to say I'm using 0.4.5


EDIT:

I went looking around and got to the screen shown in my screenshot, I told it to auto detect but its not picking up anything..... where is there just a "manage midi controllers" menu or something?

---

### Post by AutoStatic on 2010-01-11
And your MIDI settings in LMMS? You're probably using the dummy driver now.
Edit - Settings - Keyboard icon - MIDI Interface
You could use either raw or seq. What are you using as the Audio Interface?

---

### Post by Affrikka on 2010-01-11
its the dummy interface-- i cahnged it to ALSA and everything works. thank you so much!!!

---

### Post by AutoStatic on 2010-01-12
Glad I could help :)

---

### Post by JayPeeJay on 2010-01-26
Hey, I am having the same problem with midi, except when I try to change it to the alsa it won't save the setting.  I go back into the settings, and it still says dummy midi.  My alsa sound works fine, although I had to replace the default device with hw: 0,0.  Tried that with the midi setting as well but it didn't work.

Any ideas?

---

### Post by JayPeeJay on 2010-01-27
Forgot to mention that my soundcard is Ali M5451 Ac'97 and that my splash screen tells me that the ac'97 mixer is creating a problem and that it is removing the mixer.  This happens every time I boot up, but my sound works fine besides the midi.

Also it is not the program settings my midi doesn't work in general.  I am using a USB  midi man uno 1X1.

**update** installed the proper firmware, now my midi works with other programs, but I am still having the same problem with LMMS not saving my settings and defaulting to dummy.  BTW lmms doesn't come up with any alsa connections programs?  Is it supposed to?  How do you connect it to the midi device if it doesn't?

---

### Post by JayPeeJay on 2010-01-29
Okay, so I read somewhere here to kill the pulse audio and only to use ALSA, which I did, only to find that I had no sound whatsoever then.  So apparently I have been using Pulse Audio this whole time.  So I researched how to make the ALSA work, and after messing around with modprobes for about an hour I finally read that my sound card is incompatible with ALSA (despite the fact that their is a driver called 5451)?

Anyone know a good sequencer that is compatible with pulse audio?

---

### Post by AutoStatic on 2010-01-29
Your soundcard is compatible: [https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresario2100](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresario2100)

And if it doesn't work with ALSA it won't work with PulseAudio either. ALSA is the driver backend, the part that talks to your hardware, PulseAudio is  a frontend, a sound server, to which apps can send sound. PulseAudio in its turn sends everything that is coming in to the ALSA backend.

What does **aplay -l** say in a terminal? And could you also do a **amidi -l** with the Uno attached?

---

### Post by JayPeeJay on 2010-02-02
**** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31

Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 20:0    MidiSport 1x1                    MidiSport 1x1 MIDI 1

Dir Device    Name
IO  hw:1,0,0  MidiSport 1x1 MIDI 1

---

### Post by mr. poopy pants on 2010-08-13
same problem, wont save midi settings always goes back to dummy! I really wanted to use my midi keyboard with lmms. im using a 4.5 with ubuntu with an intel i3 gigabyte mobo with onboard audio. im banging my head against the wall on this one. thanks for any input!

---

### Post by prock on 2010-09-12
Had the same problem in my MIDI setup options... but then it was OK.  One thing I did that may have done the job is:
Plug in your USB keyboard controller and turn it on.  In Terminal type lsusb  ,the keyboard should be listed.  Now Start LMMS and your MIDI setup option should now change and remain after LMMS restart.  Your keyboard may now be listed in the MIDI dialog.  Mine is now working great! 

You may need to use the lsusb command each time prior to starting LMMS There is a way to automate this task but I have not done this yet.  I think this is is what made the difference for me.  There was keystroke latency but the solutions at [lmms.sourceforge.net/wiki]("http://lmms.sourceforge.net/wiki/index.php?title=Troubleshooting") Fixed it.

---

### Post by AutoStatic on 2010-09-13
> **prock said:**
> You may need to use the lsusb command each time prior to starting LMMS**man lsusb**:```
NAME
       lsusb - list USB devices

SYNOPSIS
       lsusb [ options ]

DESCRIPTION
       lsusb  is  a  utility for displaying information about USB buses in the
       system and the devices connected to them.
```
So **lsusb** only shows information, it doesn't modify or initialize anything. So no need to run it before running LMMS.

---

### Post by DDmason on 2011-04-04
Ok I have read all this and Im still completely lost. I have a MIDI Keyboard that my computer reconizes, but I have no clue how to make it work with LMMS. Please help!!!

---

### Post by jack_spratt on 2011-04-24
My M-Audio Oxygen 61 works with LMMS on EasyPeasy (based on Ubuntu 10.04).

I messed around with firmware to start with, before realising that it wasn't required, and that my keyboard was already working correctly without further configuration (testing is Rosegarden confirmed this - the key-presses were registered even though I heard no sound).

In LMMS I add an instrument, click on the spanner icon to the left hand side of the instrument track in the song editor window, then click midi > input > 20:0 Oxygen 61. Then when I play the keyboard keys the sound comes through my speakers. You may also need to enable record mode to hear the sound.

Only ZynAddSubFX instruments are working with my keyboard at the moment; I don't know why.

Hope this helps.

---

### Post by jaqmann on 2011-04-27
I have a question about LMMS- I don't use Linux, I have Windows 7 and like LMMS, but when I try to use MIDI, it fails. The computer recognizes the USB-MIDI connection, and so does LMMS, but it only shows up as USB midi interface when I try to do anything MIDI on LMMS. I only have WinMMmidi and dummywhatever for MIDI in settings, so no ALSA or whatever for me. It shows up that USB midi interface is connected and working, yet when I play nothing sounds or shows up. Can someone help? Should I get software made for Windows 7 or is there some secret to getting this to work? Thanks.

---

### Post by Pixman on 2011-06-01
Hi guys,

I'm going crazy over this.
My keyboard, a M-AUdio KeyRig 49 works in EVERY application but LMMS.

In the instruments I chose as  Midi input my keyboard (its's shown), I use my output.
What do I put in in the 'channel' field?

I can't believe why it won't work. I tried every possible combination.

I have ALSA as Sound Output and ALSA Sequencer as Midi Controller, it's the only one that's accepted, all other ones get set to dummy after a restart of LMMS.

I have timidity installed (working) and use it as output in LMMS.

Also, I enabled the tab 'MIDI' in the instrument dialog, and I even configured the keyboard-buttons correctly to the right of the options.

What the heck am I doing wrong?

In every other software it works, but I want LMMS.

> michael@latvia:~/Downloads$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
michael@latvia:~/Downloads$ amidi -l
Dir Device    Name
I   hw:1,0,0  KeyRig 49 MIDI 1


Here's some console output.

---

### Post by Pablo_F on 2011-06-01
Hi, 

I don't use LMMS but the channel in the Key Rig and in the software side must be the same. Take a look at the Key Rig handbook to learn how to shift channels.

You can double check via qmidiroute, event log. Just connect Key Rig output to qmidiroute input in the alsa tab of qjacktcl's connection window and look at the midi messages coming from the Key Rig.

---

### Post by blackhikari on 2011-06-21
make sure that your Jack settings are correct.  I use qjackctl to do this.  My keyrig 49 was not working until I opened the settings with the settings button and changed the MIDI driver to seq. Previously, that setting had been set to raw and I couldn't connect. Then, I opened up connections, went to the MIDI tab and connected my keyboard in the left box to the Midi-Through/midi_playback_1 in the right box. Then, I followed the directions in the LMMS wiki on how to connect devices and, this time, it (gloriously) worked.  It was so worth the day or so of screwing around with it.  I've worked with a lot of music stations over the years including Cakewalk and Fruity Loops.  I've only been messing with LMMS for two days and it is already my favorite ever.

---

### Post by Pixman on 2011-06-21
Hey,

i wrote it doesn't work. I was actually wrong.

With the Natty Narwhal, it worked pretty well actually.

Using timidity as output, it worked instantly with LMMS.

I could choose the input as KeyRig 49 and the Output as Timidity Port 128:0 (and others were available of course).

I'm amazed!

Ubuntu has really made everything easy. I expected more problems.
But no, just plug it in and work with it. :)

Oh yeah, my Kernel: Linux latvia 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by WasMeHere on 2011-09-01
In the Ubuntu Forums I discovered lmms and installed it from the ubuntu repository (sudo apt-get install lmms).

I found it easy to use midi keyboards with lmms compared to using the standard(?) alternatives in ubuntu studio. When playing audio and video files I have excellent sound quality, but I only get good quality from a few of the synthesizers of lmms. So my studio needs more tweaking.

---

