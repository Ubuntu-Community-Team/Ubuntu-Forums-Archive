---
title: "synthesizer/keyboard software?"
date: 2008-11-06
forum: Ubuntu Studio
---

### Post by T2manner on 2008-11-06
i was wondering if there was software for linux or even windows that i could use to make my laptop a keyboard/synthesizer basically.
i tried googling it but didn't find anything good

---

### Post by paulmerchant on 2008-11-06
For Linux, use Virtual Midi Keyboard. You'll find it as vkeybd in Synaptic. I saw a new one recently, that looked like it would be better than vkeybd, but the project was really new.

And a few synths, like ZynAddSubFx, come with virtual keyboards.

---

### Post by T2manner on 2008-11-07
that doesn't work
and it's not what i was looking for

---

### Post by paulmerchant on 2008-11-07
Here are two other projects:

[http://vmpk.sourceforge.net/]("http://vmpk.sourceforge.net/")

[http://sourceforge.net/projects/jack-keyboard]("http://sourceforge.net/projects/jack-keyboard")

I thought vkeybd stunk at first, but I went back to it after trying some of these others. It's not hard to route the midi. You can ignore it's weird little GM interface for soundfonts. And, most importantly, it's easy to create a custom key map. The default key map is really bad.

---

### Post by Stochastic on 2008-11-07
> **T2manner said:**
> that doesn't work
and it's not what i was looking for

What are you referring to by 'that'?  Zynaddsubfx or virtual midi keyboard.  The combination of those two apps seems to be just what you're looking for, but maybe I misinterpreted your original post.

As a triggering system the softwares mentioned in the above posts should do just the thing you're looking for, unless you're in the need for a sequencing trigger system (post back and I'll gladly get into sequencer recommendations)

On the front of pure synthesis synths there are a few out there for native linux.  ZynAddSubFX is a popular one, Genpo is a good organ synth, Hexter is a nice fm synth (well actually a DX7 emulator and the DX7 wasn't actually FM, so...), AMSynth, and Aeolus are also pretty good.  There are also some DSSI or LV2 (these are plugin formats) synths out there such as the Calf audio plugin pack: [http://calf.sourceforge.net/](http://calf.sourceforge.net/)  There are also a number of synthesis languages (though they're not really beginner software, so I'd stay clear of them) designed specifically for modular synthesis design (BEAST, PureData, CSound, Chuck, SuperCollider, etc..).  There are also some really nice commercial VSTi synths that run on linux that Dave Phillips (a master of Linux Audio) has written about here: [http://www.linuxjournal.com/content/discovery-vsti-analog-synthesis-linux](http://www.linuxjournal.com/content/discovery-vsti-analog-synthesis-linux)

On the front of sound-bank synthesis I prefer QSynth, it loads most of the common soundfont formats, and plays well with JACK.

If you're new to linux audio, you should look into downloading the UbuntuStudio audio metapackages (ubuntustudio-audio and ubuntustudio-audio-plugins).  They might be overkill for a hobbyist, but they include the realtime kernel preemption packages that are really needed to make audio flow smoothly in heavy synthesis environments.

Here's a somewhat more complete listing of softsynths for linux: [http://apps.linuxaudio.org/apps/categories/software_sound_synthesis_and_music_composition_packages](http://apps.linuxaudio.org/apps/categories/software_sound_synthesis_and_music_composition_packages)
And yet another list: [http://linux-sound.org/swss.html](http://linux-sound.org/swss.html)

Hope this all helps & doesn't overwhelm you.

---

### Post by T2manner on 2008-11-07
haha.
well i think you guys are getting the wrong idea.
i'm extremely new to keyboards and synthesizers.
to be honest, i just wanted to have a keyboard/synthesizer to make my own cool sounds and beats that i hear in techo songs.

---

### Post by Stochastic on 2008-11-07
If what I've suggested flies over your head then there's two possible easier routes I can suggest.

- an all-in-one music application such as LMMS, Jokosher, or Muse (Renoise might also be right what you're looking for, but that costs money)

or

- this website is lots of fun: [http://themes.hobnox.com/papaya-themes/hobnox2007/noxtool/audio/audioapplication.swf](http://themes.hobnox.com/papaya-themes/hobnox2007/noxtool/audio/audioapplication.swf)

---

### Post by T2manner on 2008-11-07
Thank you so much
from reading what LMMS is, it sounds like the exact program i want
:D

---

### Post by Redsunz on 2009-06-12
> **Stochastic said:**
> If what I've suggested flies over your head then there's two possible easier routes I can suggest.

- an all-in-one music application such as LMMS, Jokosher, or Muse (Renoise might also be right what you're looking for, but that costs money)

or

- this website is lots of fun: [http://themes.hobnox.com/papaya-themes/hobnox2007/noxtool/audio/audioapplication.swf](http://themes.hobnox.com/papaya-themes/hobnox2007/noxtool/audio/audioapplication.swf)

I was looking for something similar as well that LMMS is exactly what I was looking for as well!:D
Awesome that you can just add and remove these apps in Ubuntu and they work right out of the box. Now I just have to figure out how to use it.
Thanks

---

