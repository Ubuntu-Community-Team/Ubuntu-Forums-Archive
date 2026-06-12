---
title: "Wrong Mixers in Distro?"
date: 2013-01-15
forum: Ubuntu Studio
---

### Post by mattruby on 2013-01-15
UbuntuStudio v12.10 (Quantal Quetzl) installs containing several packages in the Main Menu > Audio Production > Mixers and Card Control desktop menu. Of them, only "Mixer" is usable on any machine. The rest are each usable only on one specific soundcard or another. Few if any machines will have all of them, and most won't have any of them.

Further, they are installed as the alsa-tools-gui package, upon which packages ubuntustudio-generation and ubuntustudio-recording depend. So if the user removes a-t-g, APT also removes a lot of the rest of UbuntuStudio. This dependency seems wrong.

Indeed, package jack-mixer is neither installed by default in UbuntuStudio, nor does it even appear in the Main Menu > Audio Production > Mixers and Card Control > Extra mixers desktop menu. Jack Mixer seems like it should be the only audio mixer installed in a default UbuntuStudio, with the other cards' mixers/configurators optional in Extra mixers. Or at least they'd be disabled in the Main Menu.

FWIW, I disabled all the other mixers in Main Menu. I installed the jack-mixer package and added it to the Main Menu > M-a-C-C alongside Mixer and PulseAudio Volume Control. Then I added to the Panel a Launcher menu containing the PulseAudio Volume Control at the top, then Jack Mixer, then Mixer. Incidentally I removed the Indicator Plugin from the panel, because its volume control offered yet another independent volume control not synced to any others, and so another place to lose a volume setting. I think the distro should by default install either only one master volume control, or configure them so they're all always synced, including keyboard keys that adjust volume/mute.

---

