---
title: "playback extremely slow and garbled in ardour"
date: 2010-12-21
forum: Ubuntu Studio
---

### Post by lastcigaretteme on 2010-12-21
I am a relative newbie in Linux and Ubuntu, but believe I have installed Ubuntu Studio correctly and have set-up Jack and other sound preferences correctly.

Play back in Ardour however, continues to be bizarre. The playhead moves extremely slow (the clock will read that only fractions of a second have passed when it's been playing for much longer.) The sound itself is nearly unlistenable, as if it's cutting in and out in a steady violent rhythm, jumping very quickly between sound and silence.

During all of this, Jack shows that x-runs have gone through the roof. I've attached a screenshot, but can upload a full text version if that's helpful.

Background on my system and set-up: I'm running Ubuntu Studio on Ubuntu 8.04, Hardy Heron, with Kernel Linux 2.6.24-rt, on an Acer Aspire 5100. Hardware has 2.2 GB memory and processor is AMD Turion 64 Mobile Technology MK-38

In sound preferences/device, ALSA choosen in all categories
Have used the test buttons, and all seemed fine except for 'sound capture'... when I tested this in sound preferences I received this message:
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat' "

jack info:   JACK Audio Connection Kit - Qt GUI Interface
Version: 0.3.2
Build: Feb 8 2008 04:48:37
----
setup:
now set to 44100
frames/period  512
periods/buffer  2
realtime enabled


hardware driver test says that 'sb' soundcard is working fine.
I believe the soundcard is HDA ATI SB

 I posted here [http://ubuntuforums.org/showthread.php?p=8172824#post8172824](http://ubuntuforums.org/showthread.php?p=8172824#post8172824)  with this issue last year and received some help, but then set aside trying to make Ardour work on this system as it was taking up too much time and could just continue using Ardour on my Mac set-up. I'm now wanting to give it another shot thought I'd repost and clarify in hopes of finding a solution.
Any advice would be much appreciated. I would love to be able to use Ardour and Jamin on this system.

---

### Post by Pablo_F on 2010-12-21
Hi,

Tons of xruns... It would be easier getting help if you had a recent version of ubuntu. I suggest you should install ubuntu(studio) lucid or maverinck for a better support and more success probabilities. Jack and ardour versions in ubuntu hardy are ancient and they have improved a lot in the last three years or so. You audio card does not help either.

In the meanwhile try increasing frames/period and see what happens. If you have a rt kernel (I think I read so in your other post) configure rtirq-init script, as per instructions in rncbc.org site. There are more hints in linuxmusicians.com wiki and jackaudio.org. 

Anyway, consider updating the software.

Cheers, Pablo

---

### Post by lastcigaretteme on 2010-12-21
Hi Pablo,
Thanks for your reply and your suggestions. I have definitely been considering upgrading, and reading your thoughts confirmed that instinct. (When I initially installed it I think the ubuntu studio version I installed was the latest 'stable' version, and when I returned recently, their site still said it's the version they recommend. Perhaps I read it wrong?) At any rate, an upgrade sounds like it's definitely in order.
My other hesitation in upgrading to Lucid or Maverick is (because I am so new to Linux and Ubuntu) I'm not sure how that will affect current documents, etc, that I have on this computer. Will such an upgrade act like a 'clean install', making it necessary to reimport files and applications not already in the Ubuntu Studio package?
If so, I want to make sure I've got my ducks in a row before I do it.
This newbie definitely appreciates any guidance on that front.
Now I'm off to take a look at your suggestions about configuring the rt kernel, etc...
Thanks again for your help.
Cheers

---

