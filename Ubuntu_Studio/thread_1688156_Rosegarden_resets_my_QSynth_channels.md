---
title: "Rosegarden resets my QSynth channels"
date: 2011-02-15
forum: Ubuntu Studio
---

### Post by _oscar_ on 2011-02-15
Hey all,

Another newbie question (at least... when it comes to midi ;)
I created a few synths in QSynth, each with 1 or more soundfonts. I assigned programs to each channel and saved them as default (all in QSynth).
Then I happily record a few tracks.

Next time when I start all my apps, often (not always ??), all channels in QSynth are reset to the first program of the soundfont at offset 0. Sometimes I see them being reset at the moment I play the song from the beginning, but also when I select a track in rosegarden.

I know this must be described somewhere, but I haven't found the proper search keywords yet :-S
Any help is appreciated!

---

### Post by _oscar_ on 2011-02-15
It looks live I've found it already, but that still leaves me with a question.
In the synths I created, I had loaded more than 1 soundfont file, using the offset to assign different bank nrs.

I did not use the banks in Rosegarden (yet); wanted to set that up when my synths are final, so I just assigned sounds from a bank to a channel in QSynth and in Rosegarden just select the device and channel, ignoring the instrument options (bank/instrument dialog)

What I did now, is load a single soundfile in the synth and use that same file to import the banks in Rosegarden. Now I can select (and save!) whatever I like in RG.
I tried to do the same with multiple soundfonts adding more banks (where LSB eqs the offset), but that doesn't work.

Question that remains... is what I try to do here indeed only possible when I use a separate synth for each soundfont?

---

### Post by Pablo_F on 2011-02-16
Hi Oscar, 

I am not sure about your question, just an idea that could simplify your workflow:

Instead of an external fluidsynth frontend, you can use fluidsynth as a dssi plugin (synth plugin) inside Rosegarden. You need fluidsynth-dssi package. 

Cheers, Pablo

---

### Post by piovezan on 2011-02-16
Yeah that's what I'm doing too. My first attempt (since "Rosegarden produces no sound by itself" and blah blah blah) was to rely on Qsynth for setting up the instruments and assigning them to each MIDI channel, but Rosegarden would keep screwing my setup and resetting the channels whenever I pressed the Play button. Synth instruments would work though, so I decided to setup one fluidsynth dssi plugin (which loads an instrument from a soundfont) for each one of the channels and voilà!

---

### Post by _oscar_ on 2011-02-16
I currently got it working fine with 1 soundfile per synth, but I also have a few soundfiles with only 1 instrument. I think it's ridiculous to create too many synths, so I wanted to group them in a single qsynth instance.
Well... that doesn't work :-/

The DSSI plugins doesn't work either; it just produces white noise. I googled for that; it's a known bug, so I'll wait for the next update.
Thanks for your replies.

---

### Post by _oscar_ on 2011-02-17
I think I found my solution :-D
I downloaded fluidsynth 1.1.3; that solved the white noise issue in the DSSI plugin ([https://bugs.launchpad.net/ubuntu/+source/fluidsynth/+bug/659112](https://bugs.launchpad.net/ubuntu/+source/fluidsynth/+bug/659112)), but I quickly found out multiple channels use the same plugin instance where I still can load only 1 soundfont, so that was it.

I now got it running fine with multiple soundfonts, all with just 1 program, in 1 QSynth instance.
At first that didn't work 'coz I had more instruments with bank 0 and program 0; the offset to bring a sound to bank1/program 0 doesn't work, since it looks like Rosegarden always selects the sounds from bank 0.

I now used Swami to give all sounds in all files a unique program number. They're all loaded in bank 0 now in QSynth, no offset, and this works great!
I manually filled the bank in Rosegarden and it all works smoothly now\\:D/

---

