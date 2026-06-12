---
title: "Rosegarden"
date: 2012-12-21
forum: Ubuntu Studio
---

### Post by DrSmash on 2012-12-21
Has anyone been able to get sound out of Rosegarden in Ubuntu Studio 12.04 or 12.10?

I use the Manage MIDI Devices menu item to map General MIDI Device to either fluidsynth or timidity.

I've recently upgraded to Ubuntu Studio 12.10 to see if the results are any better.  In both 12.04 and 12.10, I get no sound and then Qsynth freezes up.  For Timidity, still no sound (timidity will play midi files all by itself, though).  When I start Rosegarden, audio from all other applications stops working until I exit Rosegarden (in Ubuntu Studio 12.04).  In Ubuntu Studio 12.10, loss of sound persists even after quitting Rosegarden, and I have to reboot to use other sound applications.

Ubuntu Studio 12.10 32-bit
Rosegarden 12.04 (it was 11.something in Ubuntu Studio 12.04)
Intel E8400 processor/Intel Motherboard/2GB RAM

---

### Post by BcRich on 2012-12-21
Hi DrSmash
If you're using fluidsynth it might be easier to use it via DSSI instead of mapping an external instance of it, with the Manage Midi Devices dialog?
That's what I do when I use fluidsynth with Rosegarden in Ubuntu 12.04, sound works perfectly everytime :) see attached image

---

### Post by DrSmash on 2012-12-22
Thanks, but it doesn't seem to work.  I even went into editor>> Load Soundfont and loaded FluidR3_GM.sf2 or timGM6mb.sf2, and either way there is no sound.

---

### Post by BcRich on 2012-12-24
Hi DrSmash
Have you eliminated possible Hardware problems?
Do you have multiple soundcards (incl onboard and/or graphics card with HDMI)?
I need more details about what you've done to try get sound from rosegarden using fluidsynth, like are you using JACK? If you are doing this with DSSI you don't need to use JACK, however if you are trying to trigger fluidsynth externally by routing midi data to it, JACK will make this alot easier.
Can you please be more specific regarding the steps you've taken.
thanks :)

---

### Post by DrSmash on 2012-12-29
I never got the FluidSynth DSSI plugin working, but while looking into the possibility of using FluidSynth with JACK, I eventually discovered the answer.

Using QjackCtl, Qsynth, and Rosegarden seems to work if each application is started in just that order:   QjackCtl (Press the Start button once opened), Qsynth, and Rosegarden.  In Qsynth, it is necessary the first time to click Setup -> Soundfonts -> Open and choose a soundfont like /usr/share/sounds/sf2/TimGM6mb.sf2.  That seems to be all it takes for Rosegarden to play MIDI or .rg files.  And Qsynth does not freeze up when it's started up this way.

In case some troubleshooting is needed, I found this to be useful:

QjackCtl:
(Assuming Qsynth is also running already...)
In Setup, use the Preset Name "(default)", and make sure the driver is "alsa".
In Connect, Go to the Audio tab.  Expand All for everything on both sides of the window (that is, both panes).   There should be a line from qsynth "l_00" to system "playback_1", and a line from qsynth "r_00" to system "playback_2".  If the connections have not been made, click and drag from one side to the other and the connection lines will appear.  If qsynth doesn't even exist, see the next paragraph to get Qsynth properly configured.

Qsynth:
In Setup, MIDI tab, the MIDI Driver should be "alsa_seq".  In the Audio tab, the Audio Driver should be "jack".  In the Soundfonts tab, an .sf2 file should be selected.

Rosegarden:
In the Studio menu -> Manage MIDI Devices, the upper left pane, "General MIDI Device" should be "128:0 Synth input port (nnnn:0)".  The 128 might be a 129 or 130, and the nnnn could be any number, but "Synth input port" is the important part.  If "General MIDI Device" is not mapped to "Synth input port", click the "Synth input port" button in the upper right pane.  Can also double-check this by going back into Qjackctl and choosing Connections -> ALSA tab.

IMHO, instructions ought to be included with Ubuntu Studio that explain all of this.  Otherwise, it is not very useful for folks that don't have the time or patience to figure it out! :)

---

