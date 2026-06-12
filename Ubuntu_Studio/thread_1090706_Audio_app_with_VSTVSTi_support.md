---
title: "Audio app with VST/VSTi support?"
date: 2009-03-08
forum: Ubuntu Studio
---

### Post by krahenke on 2009-03-08
I haven`t seen a decent audio production software yet with proper VST/VSTi support, and I`d like to use some. Can anyone suggest me one, if there is one?

Cheers,
KraHen

---

### Post by eric71 on 2009-03-09
The next 2.X release of Ardour will have VST support via the reverse engineered Vestige headers. I'm not sure if this will allow you to record audio from VSTi's loaded in Ardour, but it seems this should be happening fairly soon. At any rate the eventual 3.0 release of Ardour will also be midi capable.

DSSI-VST will allow you to load vsts in the current Ardour and VST's and VSTi's in Rosegarden. I think this also goes for Qtractor, which is coming alo9ng nicely. Unfortunately, DSSI-VST isn't in the normal Ubuntu repos, but I'm sure if you google a bit you will come across a .deb somewhere, or an .rpm that you can use alien to convert. 
 
For now, many people do have good results running Reaper under wine with wineasio. There's some good tutorials at the Reaper forums, and I've had good luck with most of my VSTs and VSTi's using this. A very elegent program, but not open source.

---

### Post by Gerhardus on 2009-03-13
LMMS (Linux Multi Media Studio) can use vst/vsti. I believe it uses a wine wrapper to do this, I haven't tried it, but I've read that it does so fairly well. LMMS is available in the repositories (at least for Intrepid) and is almost exactly like using Fruity Loops. It really is a nice program. Hope it works for you

---

### Post by hansi32 on 2009-04-01
Reaper is good. Works with all my vst plugs and Instruments, too.

---

### Post by Stochastic on 2009-04-01
Do you really need VST/VSTi support? many LADSPA and LV2 plugins do more than what the average user needs.

Another app just added to the list of VST/VSTi support is Ardour (though the version in the repos doesn't have it compiled in, so you'll need to recompile yourself and turn that option on).

---

### Post by simtaalo on 2009-04-02
vst(i) support in lmms is fairly good, there are some plugins that don't work but alot do.

here is a list of tested vsti in lmms so far [http://lmms.sourceforge.net/wiki/index.php?title=Tested_VSTs#](http://lmms.sourceforge.net/wiki/index.php?title=Tested_VSTs#)

@stochastic - there are no ladspa plugins that are fully fledged instruments in their own right like alot of vsti, granted alot of ladspa effects are good and powerful.

if you do use lmms do NOT use the version in the repo's, get 0.4.3 from [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

re:reaper - its not a "proper" linux program, it gives wine as a supported platform but personally i think thats a massive cop-out, plus its not FLOSS. however both of these things do not detract from the fact that its a very good DAW, however i would not use it on my system because of those issues.

---

### Post by kayosiii on 2009-04-02
Ok the situation currently looks like this....

1) Vsts can come in 3 flavours.... They can be compiled for Mac, Windows or Linux.... (possibly there are two flavours of Mac now ppc & intel but I don't know).... The ones natively compiled for linux can be found at [www.linux-vst.com](www.linux-vst.com).... There are only a handful of these but they do exist. 

2) Some linux apps also have the ability to run VSTs compiled for windows through Emulating the windows libraries enough for most (but not all) things that a VST would sanely do. This means that quite a few VSTs which were designed for Windows will run on Linux... I think there are some compatibility lists floating around on the internet such as this [http://ladspavst.linuxaudio.org/](http://ladspavst.linuxaudio.org/)

3) Due to licensing comparabilities with the developer toolkit for VST and limitations on its distribution coupled with the terms of licensing for most free software. It was not possible to ship applications with VST support enabled - The developer toolkit has been reverse engineered recently so this limitation no longer exists. But support is yet to hit the binary version of most applications and things haven't necessarily been tested as much as they should be for a production system.

4) I am not 100% sure on this but - VST support might not necessarily mean you get the bright and shiny interface that comes with the VST plugin. It used to be that you just got a row of faders with the names of the parameters on it. (hey some people even prefer the minimalist approach) I have recently seen screenshots of apps running the pretty plugin dialogs so this might no longer be the case.

Is it that you have specific VSTs that you want to run? if so the best thing to do is to test those against the software you want to use. If you want a system that will take any VST you throw at it, well nothing in linux is at that state yet. You do with plugin vendors who specifically support linux but that is it.

If you really do still want to give audio on Ubuntu a shot then I will give the following advice. There are a few hundred plugins of varying quality in linux native formats (ladspa, dssi (softsynth) and the newer lv2)... These cover most audio editing needs there are some holes (no equivalent to Native Instruments for example). The interfaces are quite spartan - This makes it more difficult to "wing it" so understanding how things like compression, parametric Equalization etc are supposed to work really helps. There are a number of good books that cover this... Bob Katz's "Mastering Audio, the art and and the science" helped me.

---

### Post by simtaalo on 2009-04-03
> **kayosiii said:**
> 
3) Due to licensing comparabilities with the developer toolkit for VST and limitations on its distribution coupled with the terms of licensing for most free software. It was not possible to ship applications with VST support enabled - The developer toolkit has been reverse engineered recently so this limitation no longer exists. But support is yet to hit the binary version of most applications and things haven't necessarily been tested as much as they should be for a production system.


not true, lmms and now ardour use the vestige header which means it can be shipped with vst support enabled. its one of the big changes in ardour 2.8 but has been in lmms for a while now.

its been tested quite alot in lmms, and more everyday. as i said alot of the vsti's i test do work.

---

### Post by kayosiii on 2009-04-04
reread what I just wrote -  that is pretty much what I just said. Except the bit about LMMS having it for a while... because LMMS locks up on me every time I try to start it running jack... (why does portaudio hate jack so much)

---

### Post by simtaalo on 2009-04-04
> **kayosiii said:**
> reread what I just wrote -  that is pretty much what I just said. Except the bit about LMMS having it for a while... because LMMS locks up on me every time I try to start it running jack... (why does portaudio hate jack so much)

yeah jack isn't all that great on lmms because devs have other priorities and alot of us aren't too bothered bout jack support.

although jack is reportedly better in 0.4.3 than previous versions.

---

### Post by kayosiii on 2009-04-04
It sure sucks if you are using a firewire soundcard though

---

### Post by aaron76 on 2011-04-17
Renoise is cross platform but I think you still a vst wrapper for full support.

---

### Post by overdrank on 2011-04-17
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

