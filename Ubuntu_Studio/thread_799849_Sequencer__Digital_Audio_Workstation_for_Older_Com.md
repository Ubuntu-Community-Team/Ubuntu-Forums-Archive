---
title: "Sequencer / Digital Audio Workstation for Older Computer"
date: 2008-05-19
forum: Ubuntu Studio
---

### Post by jethin on 2008-05-19
Howdy,

I'm running Xubuntu 8.04 Hardy on an older 700 Mhz AMD Compaq with 256 MB RAM. I'd like to do some music production on this computer (how's that for optimism?) but as I'm new to Ubuntu I'm wondering if someone could recommend:

1. A Sequencer/Digital Audio Workstation that might work well on my machine (i.e. not too resource heavy but with a decent feature set including basic effects). Rosegarden seems nice to me, but I think it might push my machine to its limits. FWIW I used to record/edit both audio and MIDI using older versions of Sonar/Acid when this was a Windows machine.

2. What sorts of Ubuntu mods/packages I should install to prep my system to run whatever application I select? I'm thinking stuff to reduce latency and maximize resources.

Thanks for your help. I'm looking forward to getting this old box grooving. Jeremy

---

### Post by robeast on 2008-05-20
You'll want to follow some of the steps from the Ubuntu Studio Preparation page:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
such as installing the realtime kernel and setting audio group access and priority. As for what program to use, I think you would have to experiment. I would assume that using too many effects or running too many tracks at once would slow things down, but not necessarily the choice of application. Check out what's listed at [http://www.linux-sound.org](http://www.linux-sound.org)

---

### Post by thorgal on 2008-05-20
I think they forget to mention a word about IRQs : interrupt sharing and IRQ / timer thread priority. They may want to add a pointer to the script rtirq and an app called irqbalance, that work well with an RT kernel. I get more reliable results in my own studio thanks to some of these IRQ tweaks.

---

### Post by eric71 on 2008-05-20
You might try Qtractor. It is much younger than Rosegarden, but is coming along nicely. Much lighter too. And the developer always has a .deb for each new release.

[http://qtractor.sourceforge.net/qtractor-index.html](http://qtractor.sourceforge.net/qtractor-index.html)

---

### Post by Stochastic on 2008-05-21
> **eric71 said:**
> Much lighter too.

Saying it's lighter than Rosegarden is like saying something is less expensive than building a man-made island resort off the coast of Dubai.  Though Jethin did ask for something lighter than and similar to Rosegarden, so you're comment is totally valid in this context.  I just find it funny.

If you're strapped for computing resources keep your eyes on the libraries you're using for each app.  Try - if at all possible - not to use too much variety in libraries.  The best thing would be to not use gui whenever possible (it can be done easily with jack for instance) but this can be very difficult for a beginner to linux.  The other approach I'd suggest is, instead of non-linear editing, attempt to do as much work as you can in separate steps; this will lower your flexibility in production but may be worth the savings in resources.  If you HD is big enough save each step as a separate file to gain back a bit of flexibility.

Audio processing is a computationally intensive task, midi synthesis is also draining (depending on the synthesis method used - which fairly directly correlates to the sound quality), so be as wise as you can in separating tasks.  Lots of apps will run on your setup, but if you attempt to do too much stuff at once, expect things to bog.

Oh and make sure you setup a bit of extra swap space for those moments when your load starts to bulge too much.

Here are some great websites that list tons of low-resource audio/midi apps (though some are not terribly pretty, or for that matter usable):
[http://apps.linuxaudio.org](http://apps.linuxaudio.org)
[http://linux-sound.org/](http://linux-sound.org/)

If you get really into this project I'd even recommend installing a different OS, as Ubuntu (even Xbuntu) can be pretty bulky as far as linux distros go.  Then again, if you find a setup that works, no need to switch.

---

