---
title: "timidity"
date: 2009-12-14
forum: Ubuntu Studio
---

### Post by MichaelBurns on 2009-12-14
I installed timidity through synaptic.  I don't know how to use it yet.  I don't even know how to launch it.  There is no menu item in the applications menu, and when I enter "timidity" on the command line, it just tells me about itself.

Anyone using timidity have any advice?

I must admit, I'm not even quite sure what timidity is supposed to do.  I had anvil studio on my windows setup (on this same computer), and that did pretty much what I wanted it to do:  piano roll and sheet music editting, midi capture from external device, midi playback both through my soundcard and through external device.

---

### Post by Tricity on 2009-12-14
Timidity can be seen as a "converter" from MIDI to sound. Timidity is a lightweight MIDI player/synthesizer that uses wavetables (=soundfonts). I suspect that Timidity is running on your system in the background (do you have a file /etc/rc5.d/S99timidity ? Can you do a ps aux | grep timidity ? Can you see timidity ports in Jack?)

Timidity accepts either input from a MIDI file or from a MIDI device (e.g., through JACK). 

I found timidity unusable in live use of ubuntu-studio because it has a considerable lag. Instead, I use fluidsynth.

---

### Post by MichaelBurns on 2009-12-14
Tricity, thank you for your prompt reply!

> **Tricity said:**
> Timidity can be seen as a "converter" from MIDI to sound. Timidity is a lightweight MIDI player/synthesizer that uses wavetables (=soundfonts).I didn't know that there was any other way to play midi through the soundcard.  Are you saying that this is the ***only*** thing that timidity does?  If so, then I am looking for something else - something with more features (like Anvil).  The timidity website makes it seem like it does more than this.  False advertisement?

> **Tricity said:**
> I suspect that Timidity is running on your system in the background (do you have a file /etc/rc5.d/S99timidity ?Yes.  It's a link to a script.  What does that have to do with it running in the background?

> **Tricity said:**
> Can you do a ps aux | grep timidity ?
root      2926  0.0  0.4  14408  4868 ?        S    10:33   0:00 /usr/bin/timidity -Os -iAD

> **Tricity said:**
> Can you see timidity ports in Jack?)I have no idea what that means.  Please keep in mind that I'm "new" to "Linux", and I only dabble in midi.  (I've been trying to learn for a few months now, but it still frustrates me every day, and I am constantly hearing terminology, e.g. "timidity ports in Jack", that makes no sense to me.)

> **Tricity said:**
> I found timidity unusable in live use of ubuntu-studio because it has a considerable lag. Instead, I use fluidsynth.Lag?  Does that mean sluggish?  I hate sluggish.  I may try this fluidsynth of which you speak.  The two alternatives that I had in mind, though, were ardour [corrected from "arduous"] and rosegarden.  Do you know about either of those?

UPDATE:
I uninstalled timidity and installed fluidsynth.  Apparently it is called QSynth in the Applications > Multimedia menu.  When I tried to launch it, it told me that there was an error because it couldn't create the audio driver Jack.

In the Audio tab in the Setup menu, Jack is one of four options (which also include alsa and oss).  So, why can't I just choose alsa, say?  Why is it an error?

How do I create a midi sequence?

---

### Post by Tricity on 2009-12-19
OK, many questions. Under Linux, sound and MIDI are somewhat... different.

First, you are using xubuntu. This may cause a problem, because you need a so-called low-latency kernel, that is, a kernel that allows specific applications to respond near real-time. Such a kernel often ends in -rt (e.g., linux-kernel-2.6.31-9-rt) - if you don't, you won't have much joy with your music apps.

In that case, I'd recommend installing ubuntu-studio (or if you absolutely want to keep xubuntu, install the ubuntustudio-audio package).

Now about Jack. Everything revolves around Jack here. Jack is a low-level connection kit (JACK stands for Jack Audio Connection Kit), and Jack allows you to connect your devices - for example, a MIDI keyboard to Fluidsynth (yes, Qsynth is right, this is a Fluidsynth GUI). Or to connect the audio output from Fluidsynth to your system - just like patch cables. That is, if you use qjackctl, the Jack GUI.

Ardour is AFAIK a wave file player and recorder. Rosegarden is a damn nifty note editor / MIDI sequencer.  In a typical setup, you'd have a configuration like this:

1) MIDI
Keyboard -> Jack -> Rosegarden -> Jack -> Qsynth

2) Audio
Qsynth -> Jack -> soundcard PCM.

If you install Ubuntu-Studio, all of this comes pre-configured.

> I wanted it to do: piano roll and sheet music editting, midi capture from external device, midi playback both through my soundcard and through external device.

Ubuntu-Studio will do this nicely. If you can spare a computer, do a clean install. Saves a lot of headache. Or use an alternate hard disk if your xubuntu box is a production machine. I found it helpful to separate studio and office/production.

I hope this answered some of your questions.

---

### Post by scinram on 2009-12-20
> **Tricity said:**
> Timidity can be seen as a "converter" from MIDI to sound. ..<clip>.. I found timidity unusable in live use of ubuntu-studio because it has a considerable lag. Instead, I use fluidsynth.

Another GEM!! ...*smile*... RT indeed!

thnx for the 'nod' Tricity.

---

### Post by MichaelBurns on 2009-12-20
Thanks, Tricity!  That is many issues to consider.  It turns out that I killed my harddrive to the point that not even the local professional could fix it, so it seems that I am indeed in a position to reconsider my choice of distro.

---

### Post by buzzstray on 2009-12-20
> **MichaelBurns said:**
> Tricity, thank you for your prompt reply!

Are you saying that this is the ***only*** thing that timidity does?



Timidity can also used as wavtable software. You can play midi file in Rosegarden and set the midi output to timidity. Actually, Rosegarden automatically do that as long timidity running on your machine. But if you still hear sound come from soundcard, you have to restart the timidity as root.

> 
sudo /etc/init.d/timidity restart


Timidity always start automatically when you are starting ubuntu. If you don't want it to start automatically, you can also disable it trough sysv-rc-conf, as root as well.

> 
sysv-rc-conf


find "timidity", uncheck the checklist.

Yet, another capability of this software is to render midi file become a wav file with a desire soundfont. Here is the example:

> 
To render all midi file channel:

timidity -Ow -o test.wav test.mid

If you have channel 1-10 filled with instrument and you want to render selected channel only, eg. channel 1:

timidity -Ow -Q 2 -Q 3 -Q 4 -Q -5 -Q -6 -Q 7 -Q 8 -Q 9 -Q 10 -o test.wav test.mid


-Ow means set the output as wav file. -Q means ignore channel... -o is output filename.

As I said, you may want to change the piano sound with one of your fav.

> 
sudo gedit /etc/timidity/timidity.cfg

add this line:
soundfont /home/me/piano.sf2 order=0



------------------------------------------------

Intrepid Ibex user

---

