---
title: "Studio: getting virtual keyboard to work with Ardour and others"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by T4_ on 2008-06-15
Hi again,

I'm trying to get vkeybd hooked up so that, when I press a key, it will play in Ardour or another audio production application. In Ardour's manual, the MIDI keyboard section states that it has yet to be written. The Audacity manual wasn't a big help either :(

I've managed to connect vkeybd to ZynAddSubFx, so that when I press a key in vkeybd, it "plays" in ZynAddSubFx; but I get stuck whenever I try to go further and connect it to an actual sequencer.

Also, coming from Windows I'm used to VST instruments/plugins, basically hardware-replacing. I've found quite a lot of LADSPA effects but no actual instruments (bass, organs, the lot). Could anyone point me into the right direction for those as well?

I'm still new to all of this, and unfortunately I work a lot so I don't have a lot of time to play around and test things out (hence this topic).

Any ideas will be much appreciated. Tutorials will be greeted with cookies and cake ;)

Thanks in advance!

---

### Post by Stochastic on 2008-06-17
Ardour and Audacity both do not have MIDI capabilities yet, so hooking a virtual midi keyboard up to them doesn't make much sense.  You'll want to hook it up to a synth program like ZynAddSubFX or a soundfont program like QSynth, then connect the audio output of those (via patchage or qjackctl's connections window) to the input of Ardour/Audacity.  You may want to take a read through here: [https://help.ubuntu.com/community/HowToSeq24Introduction](https://help.ubuntu.com/community/HowToSeq24Introduction) to get to know some basics of working with Seq24 (one of many sequencer apps in linux) - but be warned that page was created many moons ago, so some differences may exist in current versions of software.

---

### Post by T4_ on 2008-06-17
Ahh, I'm so stupid - I just had Patchage open yesterday and completely missed the point :|

I'm currently using the girlfriend's annoying Vista laptop at work, but I'll be sure to give that a try tomorrow - thanks!

---

