---
title: "music from computer keyboard?"
date: 2009-05-13
forum: Ubuntu Studio
---

### Post by scradock on 2009-05-13
I'm looking for a very simple little program that allows me to type on the computer keyboard and produce musical tones; ideally to record the output as well. The wrinkle is I want to be able to specify the exact frequency for each key, and to change them easily, perhaps from a text file.

I am sure there are programs that do this, but the ones I have checked out are geared to much more elaborate functions, and are therefore huge and would take a long time to get inside so that I could do what I want - use non-standard intervals. Rosegarden, for instance, requires me to download and install over 600MB of files, even in a Kubuntu-enabled machine.

Any ideas? I've looked at gcomposer, which promises simplicity, but requires to be compiled. I'm stuck at the instruction "do a make", when there is no makefile.........

---

### Post by Stochastic on 2009-05-13
In many cases such a specific task is quite easy to build in a programming environment like PureData.  I whipped this one up in half an hour though it's not really complete (hopefully it's self explanatory enough for you to finish it for a full keyboard and multiple tuning systems).

To run, install pd: sudo apt-get install puredata
Untar the file (the forums require a tar extension).
Open the patch.

If a note sticks on, you may need to switch in/out of edit mode (ctrl+e is the shortcut) so that you can click off the stuck toggle box.

Oh, and to extend beyond an octave use the [* 2] object to multiply the frequency by 2 (or 4... [* 4] )

I know, it's a bit of work (not really that simple) but you'll get lots of flexibility this way, and it's probably simpler than writing a makefile for gcomposer ;)

---

### Post by scradock on 2009-05-13
Thanks - that looks like a good place to start! I haven't got it to make a sound yet, but I do have it running, and I guess it will take me a while to set everything up - have to try to understand it first. At the moment I must be in edit mode - anything I type overwrites the stuff in lttle boxes.....

---

### Post by Stochastic on 2009-05-13
Yeah, head out of edit mode to use it, into edit mode to fix/add to it.

For sound preferences, see the main PD window (the menus at the top).

If you have some time to do some reading, this book by the author of PD can explain quite a bit: [http://crca.ucsd.edu/~msp/techniques.htm](http://crca.ucsd.edu/~msp/techniques.htm)

---

### Post by scradock on 2009-05-13
Thanks again -

---

### Post by scradock on 2009-05-18
OK, got it running now. I've added more oscillators, and set two alternative tunings. It does fine with single notes..... trying to play two simultaneously doesn't give nice chords, unfortunately.

I've tried running two separate instances, but the second one doesn't make any sound - presumably the first one grabs the audio channel and can't share.

Anyway, it does do what I asked for, and I'll go on playing with it and see if I can extend it further.

---

### Post by markbuntu on 2009-05-22
Try freewheeling, you can assign keys to notes, instruments, files etc etc. It is a very simple to use live looping instrument with recording capability. There is a very good set of tutorial vids you can just watch first and see if it is what you are after.

---

### Post by scradock on 2009-05-22
Thanks!

---

### Post by mjpatey on 2009-05-24
You may like to try zynaddsubfx, available from one of the standard Ubuntu  repos.  More info about it is here:

[http://zynaddsubfx.sourceforge.net/](http://zynaddsubfx.sourceforge.net/)

It's a software synthesizer that you can play with either MIDI input from an instrument or file, or by playing the notes on the computer keyboard.

You can also search Synaptic for vkeybd, a virtual keyboard that can be patched using JACK to send MIDI messages to virtual modules, etc.  I don't know if it can be played with the computer's keyboard or not (maybe just mouse), but it's worth a look.

Happy hunting!

-Mark

---

