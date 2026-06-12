---
title: "MIDI bank sound sampler"
date: 2009-04-28
forum: Ubuntu Studio
---

### Post by LitusMayol on 2009-04-28
Hi everyone!

I'm loking for a MIDI program able to be programmed with a nice MIDI bank sound. I've used *Reason* in Windows an it is awsome and I'd like to find one similar. 

Till now I've only find *Rosegarden*, but I have always problems with the sounds. 


Can someone recommend me one?

Thanks buddies!

---

### Post by eye208 on 2009-04-28
You can use ZynAddSubFX (a software synthesizer), Qsynth (a SoundFont player), Hydrogen (a drum sampler) and several others. They are standalone programs, but Rosegarden can control them via MIDI and also record their output via Jack audio transport. You can use QjackCtl or Patchage to control the routing between the programs. This is pretty much the same thing as ReWire on Windows. If you have external gear (sound modules, MIDI keyboards etc.), you can connect them too.

---

### Post by barisurum on 2009-04-28
You may have a look here:

[http://ubuntuforums.org/showpost.php?p=6106850&postcount=8](http://ubuntuforums.org/showpost.php?p=6106850&postcount=8)

---

### Post by LitusMayol on 2009-04-29
barisurum eye208

Wow!

From the very beginning I never thought that amount of options, thanks both **barisurum**and **eye208**.

I'll try some and the I'll post which one I prefer!

Thanks from a newbie from Barcelona!!

---

### Post by barisurum on 2009-04-29
For some reason (why? by the way) linuxsampler is not in the repos. You may download a 64bit binary for ubuntu [here]("http://www.viciouslime.co.uk/downloads?option=com_docman&task=cat_view&gid=2&Itemid=2")

---

