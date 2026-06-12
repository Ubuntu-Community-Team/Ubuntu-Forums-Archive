---
title: "midi convert 2 mp3"
date: 2009-10-12
forum: Ubuntu Studio
---

### Post by nnjond on 2009-10-12
Hi,
Can anyone recomend a means for midi convert 2 mp3 or ogg?

Thanks

---

### Post by kayosiii on 2009-10-13
1) install and get jack running... I am fully aware that this currently a complete PITA on ubuntu.

Install a midi sequencer + the synth you want to play back the midi file. Install patchage,time_machine & audacity.

Load the midi file in the sequencer (maybe rosegarden or msscore). If necessary connect the midi output of the sequencer to your synth of choice. Connect the output of the synth to the input of timemachine. hit play in the sequencer & within 10 seconds hit the record button in timemachine. wait for the midi file to play, hit the stop button in timemachine (it only has one button). This will create a w64 file in your home folder starting with the letters tm. You can open this in audacity and convert it to what you need (you can also make some adjustments here).

That's how I would do it anyways.

---

### Post by mcduck on 2009-10-13
> **nnjond said:**
> Hi,
Can anyone recomend a means for midi convert 2 mp3 or ogg?

Thanks

Timidity allows you to do that. But, you should be aware that since midi isn't actually audio format at all the result might sound quite different than what you expected, depending on your midi file and the instruments/soundfont used to play it back.

WildMidi is also a good one, and at least in 9.10 it comes with the gstreamer0.10-plugins-bad -package to allow playing back midi files with Totem (and other gstreamer-based players). 

Of course with both these program's you'll also need some soundfonts, the default ones leave lots of room for improvements.

---

### Post by nnjond on 2009-10-13
Thanks both of you for your advice, but i'm sorry i don't understand it.  Ithink i should make myself a little more clear:

Ihave some short Midi files i can play in Totem Movie player. I would like to play them in random on say, RythymBox, and so i must convert them. Instramentation is irrelevant. I have Audacity and Timidity,(Not very comprehensable), installed.

---

### Post by mcduck on 2009-10-13
Just open a terminal, move to where you have your midi file and run the following command:

```
timidity -Ow yourmidifile.mid
```
(that's a capital o, not a zero. And of course replace the file name with the name of your midi file...)

Timidity will create a .wav file in the same directory, and you can then convert that to .mp3 or whatever format you want.

---

### Post by nnjond on 2009-10-13
Thanks alot, that's great!  Can you think of the command for all *.mid ?

---

### Post by nnjond on 2009-10-13
Solved

---

### Post by Simian Man on 2009-10-13
You can also use SoundConverter to convert midi to a variety of formats.  This is nice because you can set the output quality and so on very easily.

I have also used [this site]("http://www.hamienet.com/midi2mp3") to convert midis before.

---

### Post by mcduck on 2009-10-13
> **nnjond said:**
> Thanks alot, that's great!  Can you think of the command for all *.mid ?

sure.

```
for f in *.mid; do timidity -Ow $f; done
```

---

