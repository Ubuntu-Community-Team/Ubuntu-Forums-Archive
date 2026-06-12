---
title: "alternative to gigasampler &amp; Kontact?"
date: 2009-12-02
forum: Ubuntu Studio
---

### Post by garyed on 2009-12-02
Is there a way to use my samples in these different formats in U-studio.  
I'm trying to make the switch from Windows for my music production. I have an older version of U-studio(7.04) that works pretty good but I haven't used it much yet. I'm not looking for any step by step instructions right now, just a little info on whether it's feasible. Between Ardour & Rosegarden they can handle my recording needs but using samples is where I'm lost. Dxi & Vst support would be nice also.
Any info appreciated

---

### Post by sgx on 2009-12-03
Hi, I have installed and used NI plugins in wine/wineasio, and used
linuxsampler to load and play giga format files. The DiscoDSP Highlife
sampler/host also works great with .wav files, and most plugins that are free of dongles, or Pace style copy protection will work. If samples are a large part of your production plans, Extreme Sample Convertor is a must-have purchase.
Its around $80, but will add years to your life. Also, Wusikststion is
implementing excellent sfz format support, and works well in linux with Reaper. Its a wonderful rompler/synth/wave-sequencer/drum-machine, with
a massive soundset, perhaps one of the truly great bargains available.

The Rakarrack multi-fx app really puts the frosting on whatever sounds you feed it.

 The easy Hydrogen drum machine has 24 kits at last count, and
is great for creating new custom beats on the fly.

The zynaddsubfx multi-timbral softsynth is easy to create wonderful dreamy soundscapes, or crazed thundering metallics.

Give yourself a year, and budget for hardware known to work in linux.
Those who need miracles by the weekend, using unsupported hardware,
don't last long in a linux community. 

Cheers

---

### Post by garyed on 2009-12-03
Thanks for all the great info,

I've been moving over to Linux gradually. 
For the last two years or so all my computers have been using Ubuntu for everything except music production so I'm familiar with the OS now.
I've gotten jack working good with an M-audio Audiophile 2496 & syncing midi works fine between Ardour & Rosegarden. I've just been hesitant to make the switch until I can get my samples working. I'd like to stay away from Wine as much as possible for music work if I can. 
I was hoping that Linux sampler could do what i wanted without the need for Wine.

---

### Post by GraysonPeddie on 2009-12-03
Keep your mind open! If you do a search for VSTi-/DXi-equivalent DSSI softsynths, you might think less about Windows for music production! :)

---

### Post by sgx on 2009-12-03
> **garyed said:**
> Thanks for all the great info,

I've been moving over to Linux gradually. 
For the last two years or so all my computers have been using Ubuntu for everything except music production so I'm familiar with the OS now.
I've gotten jack working good with an M-audio Audiophile 2496 & syncing midi works fine between Ardour & Rosegarden. I've just been hesitant to make the switch until I can get my samples working. I'd like to stay away from Wine as much as possible for music work if I can. 
I was hoping that Linux sampler could do what i wanted without the need for Wine.

Hi, linuxsampler is native for linux (and windows/0sEX) but I probably jumbled the wording. The developer and mailing list are active, I think sf2 support is coming, and DigitalSoundFactory has a huge Proteus
library 3500+ sounds in that format. The giga format works well, I have read where the popular GigaPiano works great. There are different gui called Qsampler and Fantasia, and you can try the windows version in the meantime.
Cheers

---

### Post by DerickX on 2009-12-07
Yeah LinuxSampler is the way for you.

Besides that, you can try to use your VST plugins on Linux via FST or dssi-vst or wineasio.

But I recommend you to check what is possible on Linux native first!

---

