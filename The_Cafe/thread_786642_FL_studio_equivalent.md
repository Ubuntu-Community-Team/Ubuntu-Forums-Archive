---
title: "FL studio equivalent?"
date: 2008-05-08
forum: The Cafe
---

### Post by sujoy on 2008-05-08
Is there a FL Studio alternative for Linux?

[http://www.flstudio.com/](http://www.flstudio.com/)
[http://en.wikipedia.org/wiki/FL_Studio](http://en.wikipedia.org/wiki/FL_Studio)

Its for creating music with a number of musical instruments like drums, guitars, organs, etc.

EDIT: so far i have heard of rosegarden and LMMS, anyone using these?
now while rosegarden needs kdelibs, LMMS wants wine!!
ain't there any native gnome app or gtk?

---

### Post by SuperSon!c on 2008-05-08
as much as i'd love to see an equivalent, i'm not about to relearn another piece of software after getting comfortable with fruity loops and some other music apps.  virtual machine works great for my needs. if you find out that one of those others are pretty good (won't be as good as FL though) i'd like to hear about it.

---

### Post by NineKnuckles on 2008-05-08
I know there are alot more out there, but Rosegarden is good - works well with instruments, and I've been using Audacity for alot basic things (although it can be used for alot of advanced things) before migrating to ubuntu.

---

### Post by Delever on 2008-05-08
Does anybody know about VSTi and if it would be at least practically possible to develop support for VSTi (or VST) plugins without emulating windows libraries?

---

### Post by sujoy on 2008-05-08
> **SuperSon!c said:**
> as much as i'd love to see an equivalent, i'm not about to relearn another piece of software after getting comfortable with fruity loops and some other music apps.  virtual machine works great for my needs. if you find out that one of those others are pretty good (won't be as good as FL though) i'd like to hear about it.

by virtual machine, you mean something like virtual box?

---

### Post by BDNiner on 2008-05-08
I wish there was a replacement for FLStudio for linux. I am not too fond of rose garden, mainly because i have not had time to really get into it. But also my m-audio sound card is not supported in linux and my midi keyboard and fatboy don't work in linux either. I know there is a way to get the midi keyboard working with timidity but i have not sat down and figured out that either. Man there is too much to learn in linux, i love it but if i could quit my job and work on it exclusively then i would be happy.

---

### Post by SuperSon!c on 2008-05-08
> **sujoy said:**
> by virtual machine, you mean something like virtual box?

yessir!

---

### Post by techrush on 2008-05-08
Simply put linux audio software is at about the same point windows audio software was at 10-11 years ago. There is nothing even remotely close to what fruity loops studio is capable of on linux. 

Ive been following linux audio production software pretty closely for the past few years and hate to say it but i dont see the situation improving much in the short term. 

That being said it -IS- possible to create professional quality work entirely in linux if you are willing to put in the time and effort. I know because ive done it and actually managed to sell some music i did in linux :) </brag> 

This app looks cool: [http://www.xt-hq.com/](http://www.xt-hq.com/) 

They have a native linux client and it appears to be the best all in one type solution available right now. 

The direction linux is going for audio stuff though is using dedicated apps for each component of your studio and tying them together with a professional audio server called jack. When i was doing a lot of audio work on linux my setup was: ardour (great multi track audio editor), seq24(sequencer), specimen(sampler) and the zynaddsubfx soft synth. 

My advice if you are remotely serious about audio is to keep a XP install to run FL but definately tinker with the linux stuff that is available. It wont be as slick as what you are used to but you can do some cool stuff and i found the different way of working produced some results i never would have come up with under windows. good luck :)

---

### Post by schtufbox on 2008-05-08
I just use Reaper in Wine. The developers even list Wine as one of the supported OSs as they develop it with Wine in mind I guess. Most of the VST(i)'s I used to use in windows work too :)
[www.reaper.fm](www.reaper.fm)

---

### Post by SuperSon!c on 2008-05-08
> **schtufbox said:**
> I just use Reaper in Wine. The developers even list Wine as one of the supported OSs as they develop it with Wine in mind I guess. Most of the VST(i)'s I used to use in windows work too :)
[www.reaper.fm](www.reaper.fm)

stfubox would have been a cool name.

---

### Post by maniacmusician on 2008-05-08
While there's nothing close to a direct equivalent, I think there are different pieces of software that can work together to create things of similar caliber.

One thing I do know, Hydrogen is the king of drum synth. Amazing program once you get a hang of the interface.

---

### Post by BDNiner on 2008-05-08
What sound card do you use for linux? I have been using my on board to mess around with Hydrogen but there is a hiss in the background, you really hear it on the hi hats. My m-audio USB sound card does not work in linux. i would not like to purchase a new sound card, but seeing how long it takes m-audio to come out with linux drivers, i may have to purchase a new one.

---

### Post by maniacmusician on 2008-05-08
I haven't tried it in a while, but there was no hiss for me. I have a generic onboard soundcard; [http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=44](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=44)

---

### Post by HangukMiguk on 2008-05-08
I have had no problems at all with LMMS since migrating.  As far as learning curves, I have had none migrating from FL to LMMS, as its interface as close to FL Studio as you can possibly get without using FL itself.

If you install wine, you also have the option of importing VST plugins into LMMS.

I think if you're looking for an alternative to FL Studio, LMMS is what you'll want to try.

ALSO IIRC, LMMS only needs Qt libs.

Sadly I haven't found an LMMS equiv for GTK, but I've had no problems with Qt, except that it doesn't properly blend with a GTK interface.

---

### Post by TBOL3 on 2008-05-08
Well, I like rosegarden, but it's more of a notation editor, not a sequencer (despite what the website says).  One thing that I HATE about rosegarden is dynamics.  Previous to the current version, the only way to get dynamics was to export it to a midi file, convert the midi file to a .wav, or other audio file.  Then open up audacity, and change the volume from there.  (Or you could set up a jack server, but I cannot get that to work, if any of you would like to help me with that, I would appreciate it very much), (Oh, you could also add dynamics as text to be printed out).  Now there are simple dynamics enabled.  But to get them, you  have to enable a bar, which has sliders you move up and down for every note.  Not to mention that you also have to still add the text.  I would prefer if it did it for you in one step.  (I know NoteEdit will do that for you, but it's missing MANY crucial functions such as Copy/Paste, and I know that there are other programs that will do that as well, but they only allow inserting ONE note in a beet, or one duration (I need say a half note on top, and two quarter notes on the bottom, same staff).

As you can see, I prefer note editors to sequencers.

Oh, BTW, rosegarden does have a sequencer built into it, but it's not the default.

---

### Post by techrush on 2008-05-08
i just tried LMMS again. it only wants wine to use vsts the one time i tried it lmms crashed.

lmms seems like a pretty good solution. if they had some basic effects you could use with it like reverb compression delay etc you could actually make some music with the thing.

---

### Post by sujoy on 2008-05-08
thank you for all the answers.
well i am going to have a look at LMMS and then maybe have a go at the setup suggested by techrush,

> ardour (great multi track audio editor), seq24(sequencer), specimen(sampler) and the zynaddsubfx soft synth.

---

### Post by maniacmusician on 2008-05-08
psst! don't forget hydrogen!

---

