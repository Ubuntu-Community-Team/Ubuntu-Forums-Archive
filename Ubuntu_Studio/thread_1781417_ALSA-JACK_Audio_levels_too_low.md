---
title: "ALSA-JACK Audio levels too low"
date: 2011-06-13
forum: Ubuntu Studio
---

### Post by Flaggmann on 2011-06-13
I have Acer Aspire with internal o/b sound card. Using 10.04 and 10.10 sound was good at 65%. Now after update to 11.04 vol set to 97% and I can just barely here audio. Tried alsa mixer CLI and set all to max with no red/distortion levels and still very weak. Can't understand it, box h/w is same as it was just before upgrade button was pushed.

Can anyone recommend a good sound editor with decent noise cleanup capabilities? I have tried one in Pinnacle Studio ( a plugin called SoundSoap) that was an awsome thing, it allowed you to pick a sample of the noise, then preview live as you tuned out the noises.
Have never been able to get a copy to install since. Possible one of the more complex linux audio production/editor suites might have something similar.

Thanks

---

### Post by desktorp on 2011-06-13
Have you played with the graphical mixer at all?  Check for a dropdown menu that says something about playback and see if you missed a level somewhere.  If it were a specific program, like a music player, I'd ask about preamp and the equalizer settings, but yeah.  Sounds pretty annoying.  Keep us updated and if you can muster the energy, try a clean install, because upgrades suck.

---

### Post by sgx on 2011-06-13
> **Flaggmann said:**
> I have Acer Aspire with internal o/b sound card. Using 10.04 and 10.10 sound was good at 65%. Now after update to 11.04 vol set to 97% and I can just barely here audio. Tried alsa mixer CLI and set all to max with no red/distortion levels and still very weak. Can't understand it, box h/w is same as it was just before upgrade button was pushed.

Can anyone recommend a good sound editor with decent noise cleanup capabilities? I have tried one in Pinnacle Studio ( a plugin called SoundSoap) that was an awsome thing, it allowed you to pick a sample of the noise, then preview live as you tuned out the noises.
Have never been able to get a copy to install since. Possible one of the more complex linux audio production/editor suites might have something similar.

Thankssave your sanity and go back to what worked.

Audacity has that type of noise removal, plus various EQ plugins,
low and high-pass filters etc

ladspa, lv2, and plugins: amb caps fil vco swf tap
calf plugins
inovada plugins

should all be installed. Many will appear in the audacity menu, select
the audio, then choose the plugin, take notes of good numeric values.

Cheers

---

