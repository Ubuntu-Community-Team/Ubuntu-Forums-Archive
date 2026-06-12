---
title: "i really loved ubuntu"
date: 2005-11-05
forum: Testimonials &amp; Experiences
---

### Post by supadodger on 2005-11-05
i went through alot the past 2 weeks, i went from breezy/xp dual boot to just breezy, then recreated my windows partition so i could image my breezy partition.

so i planned on leaving the duel boot but just using breezy.

so i went off in search of an audio editor of soundforge caliber.

2 weeks later i found nothing worthy.


this is of course not the fault of ubuntu, which is really great.

in my opinion the only reason ALOT of people (at least people i know) cant switch to linux full time is audio or video editing.

---

### Post by kvidell on 2005-11-05
Well, I can't really help you with Video editing as I know nothing about it... but as for audio...

There's always the old standby, Audacity.. it's mostly for sequencing and editing though... if you want something more like SoundForge (which audacity very much is), or say... FruityLoops... LinuxMagazine this month is running an article on a piece of software they just found called the "Linux Multimedia Studio", or LMMS...

It looks, from the article, to be just like FruityLoops in a lot of ways...
It doesn't appear to be in the repostories, but it's probably not too hard to compile (I'd be happy to help you if you asked pretty, maybe offered a cup of hot cider.)

Their website is [http://lmms.sourceforge.net](http://lmms.sourceforge.net)

Hope this helps!
- Kev

---

### Post by kvidell on 2005-11-05
Looking again, there's a Debian/SARGE .deb package available...
I'll see how well that installs and report back (if you're interested in it).
- K

---

### Post by supadodger on 2005-11-05
audacity was okay but i need to "stretch or squeeze" audio accurately down to the millisecond, if it wasnt for that i would make due with audacity.

ill give lmms a try and see if it can do what i need.

---

### Post by kvidell on 2005-11-05
Ah, okay..

Well, I just installed LMMS... It's pretty.
To install it I had to download both of the .deb files offered (lmms and lmms-common), and manually install two packages from the repositories:libsamplerate0 and libsdl-sound1.2.
After that, using sudo to dpkg -i lmms-commoon, then lmms and it was ready to go.

Seems like a neat piece of software.
- Kev

---

### Post by supadodger on 2005-11-05
well you seem very knowledgable and since this kinda turned into a tech support thread let me ask you one more question.

i was gonna just use vmware to load soundforge but i could never get it to use my host sound, it said it had sound but it never worked.

any quick fix for that?

---

### Post by bbking on 2005-11-06
> audacity was okay but i need to "stretch or squeeze" audio accurately down to the millisecond, if it wasnt for that i would make due with audacity.

try rezound (installable via synaptic)

greets

bbking

---

### Post by qalimas on 2005-11-06
I cna't get lmms to install, neither by source or the Sarge .debs.  For the debs, it tells me I need a QT lib package that isn't in synaptic, and for the source it tells me "QTDIR must be defined, or --with-qtdir option given", even though I did set that opion to /usr/lib/qt3

Edit: Nevermind :)

---

