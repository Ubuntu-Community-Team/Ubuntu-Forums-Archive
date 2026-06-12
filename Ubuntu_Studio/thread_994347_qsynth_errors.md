---
title: "qsynth errors"
date: 2008-11-26
forum: Ubuntu Studio
---

### Post by RootExposure on 2008-11-26
Hello,

I am trying to get midi working in Rosegarden without latency issues ([See Previous Post]("http://ubuntuforums.org/showthread.php?t=985113")).  I decided to try using fluidsynth/qsynth instead of timidity, since I have heard that fluidsynth works better with Jack (FYI I am new to Linux and MIDI so let me know if I am wrong about anything).

When I tried to Start qsynth after configuring it (used this [article]("http://www.linuxjournal.com/article/8354") to configure).  I get the following errors:
> fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
cannot lock down memory for RT thread (Cannot allocate memory)

I thought I might be able to continue, so I continued on through the article and configured Jack.  After configuring Jack, everytime I press a key on my Midi Keyboard I receive the following error from QSynth:
> fluidsynth: warning: ALSA sequencer buffer overrun, lost events

So I seem to be stuck with Rosegarden Midi.  The default settings (which I believe use timidity) have serious latency issues and setting up Qsynth has been a failure.  Pretty much just trying to get a program up and running so that I can do a Live Midi recording.

Thanks

---

### Post by raboofje on 2008-11-27
> **RootExposure said:**
> fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
cannot lock down memory for RT thread (Cannot allocate memory) 

Sound like the 'memlock' option:

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)

If it's set up like that, make sure you're in the 'audio' group.

---

### Post by RootExposure on 2008-11-27
Thanks that got rid of the errors.  Now I just have to work on the config to get qsynth working on Rosegarden.

I found a bunch of information on these settings (limits.conf), but wondering if anyone knows what exactly these changes do in layman's terms (or Windows terms since I am knew to Linux).  Not really a big deal just thought I would ask (always like to know what I am doing).

Thanks for the help.

---

