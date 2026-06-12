---
title: "how do I apply jack-rack to single track of rosegarden?"
date: 2011-07-20
forum: Ubuntu Studio
---

### Post by newbuntus on 2011-07-20
Can I apply effects from jack-rack to a single midi track from rosegarden, and if so how? I assume this track must go through a synth first to convert the midi to audio, and then the output of that to jack-rack. The other tracks would also need to go to the synth, but would not be routed to jack-rack. So is this correct, and if so how do I set it up?

Cheers

---

### Post by Pablo_F on 2011-07-20
Yes, as long as you work with jack audio clients (jack-rack is and most soft synths too) you can connect ports "from anywhere to anywhere". You can make connections via qjackctl or patchage.

However, this setup is not comfortable comparing to what you can do in rosegarden itself by means of plugins. Note that jack-rack is a simple ladspa host (audio efects only). Rosegarden can load dssi (virtual instruments, aka synth plugins) and ladspa too.

Cheers, Pablo

---

### Post by newbuntus on 2011-07-20
Ok I think I've figured out how to do it. I have to create another midi playback device in rosegarden, then set one of the tracks to use this device, start another qsynth engine from qsynth, then connect this new midi device to the new qsynth engine right? 

Anyway, my goal is to have a guitar instrument to which i can apply various effects like flange, echo, various types of distortion etc. 
Is there a synth plugin or something that I can use for this instead of having to route an instrument from rosegarden to qsynth, to an effects processor like rakkarack, jack-rack etc?

Cheers

---

### Post by marseille on 2011-07-23
> my goal ... have a guitar instrument to which i can apply various effects like flange, echo, various types of distortion etc. Is there a synth plugin or something that I can use for this instead of having to route an instrument from rosegarden to qsynth, to an effects processor like rakkarack, jack-rack etc?

I have Rosegarden v. 10.04.2 and this is what I do to record audio and apply effects within the application *itself*:

```
Segment Parameters: Track Parameters >>
Device >> Audio: Instrument Parameters >>
<no plugin> >> Plugin window
```

Look at the left column: `SEGMENT PARAMETERS'. Under the Subtitle `TRACK PARAMETERS' go to the `DEVICE' drop-down window and choose `AUDIO'. The `INSTRUMENT PARAMETERS' section will change. Hit a button(s) that say `<no plugin>'. A plugin window will pop-up; and you'll be able to choose the effects you want applied to the AUDIO.

NOTE: The plugins installed on my system automatically come up...

---

### Post by newbuntus on 2011-07-29
With a bit of googling i found the answer. I started qsynth with this command:
```
qsynth -a jack -o audio.jack.multi=yes -o synth.audio-channels=16 -o synth.audio-groups=16
```
which gives each midi channel its own L/R stereo outputs in jack, which I can then either connect to the standard system playback, or pass through and effects processor or some other utility first.

---

### Post by Pablo_F on 2011-07-29
Hi,

You can also use the gui to configure qsynth for that. 

However, I find easier just using synth plugins in Rosegarden, such as fluidsynth-dssi.

Cheers! Pablo

---

