---
title: "how to install ggseq, gungirl sequencer."
date: 2009-08-21
forum: Ubuntu Studio
---

### Post by Siljrath on 2009-08-21
gungirl sequencer is a very handy simple straight forward audio sample sequencer app.
it drives me completely barmy that it's not in the repository...
i tried compiling from source, but not being profficient in such matters, when i hit a snag, that was the end of that for me.
so then i installed alien, found myself a rpm of it and tried to convert from rpm to deb, and install it that way... it says it did it, but i cant find any way to start it up (not a binary executable in sight).

anyone successfully got gungirl sequencer installed on an ubuntu (or debian) based distribution?

if so... how did you achieve this miracle?


damn i miss gungirl sequencer.

---

### Post by Stochastic on 2009-08-22
If you've managed to turn the .rpm file into a .deb file then you should be able to install it via ```
dpkg install fileName.deb
``` or by right-clicking the .deb file and selecting "Open with GDebi Package Installer"

If that doesn't work, you can always compile the software from source.  Here is a quick introduction to doing that: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

For next time, if you find a useful app that should be in the repositories but isn't, the best thing to do is file a needs-packaging bug at launchpad.net I've gone ahead and created one for gungirl sequencer to show you what it should look like. [https://bugs.launchpad.net/ubuntu/+bug/417240](https://bugs.launchpad.net/ubuntu/+bug/417240)
This way, someone is more inclined to package it sometime soon.

---

### Post by Siljrath on 2009-10-10
well my package manager says it's installed now, but i cant seem to find an launchable file for it anywhere on my system.

anyone else tried it n got it running?

anyone know a quick fix to my nonexistant ggseq's non-executable state?

should i give it another shot with a different rpm? maybe that was problem?  (tried two now i think).

anyone know any other similar style audio sequencer's that run on ubuntu? :(

any other help or sugestions or shared experiences greatly appreciated. thnx. :)

---

### Post by Siljrath on 2009-11-08
sorry for this blatant bump.

i've made little progress with this issue so far.

it's filed as a bug, needs packaging now, so thats nice.  :)

heeeelp!

---

