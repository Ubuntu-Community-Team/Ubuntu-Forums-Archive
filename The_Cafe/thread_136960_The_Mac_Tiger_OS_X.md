---
title: "The Mac Tiger OS X"
date: 2006-02-27
forum: The Cafe
---

### Post by Connollyir on 2006-02-27
I am thinking about purchasing an Apple ibook laptop for the upcoming school year and I did a bit of research and found that the Tiger OS is based on Unix..... and can run X applications. This is pretty sweet, I am rather unfamiliar with Apple products and to find out that the Tiger OS and OS X are based on BSD is a pretty cool discovery.

The desription says that you can port applications from any Linux distrobution to Tiger which seems pretty incredible... but how true is that? I assume somwhere you run into stuff like kernel incompadibilities or something somewhere along the way.... am I wrong? 

I will be using the notebook as a companion to my desktop machine which runs Kubuntu Breezy. Am I going to have compatibility issues with software components across these two distros? Are there any problems I should be watching out for?

Is there anyone who has used Tiger here and can give me some pointers on it's pro's and cons versus Ubuntu?

And if I end up not liking Tiger, have people gotten Ubuntu to work well with the ibook? I remember seeing threads with problems related to the ibook in the past but I never really payed attention to them.

Whatever you can throw my way is really appreciated.


-Ian

---

### Post by aysiu on 2006-02-27
Fink and X11 will become your friends:
[http://fink.sourceforge.net/](http://fink.sourceforge.net/)

---

### Post by ORiON2012 on 2006-02-27
Airport Extreme will not work under Linux, which sucks. Makes things utterly useless for me at school. As for FOSS, google Darwin Ports / opendarwin and fink. There are several X11 implementations for Mac OS. The Darwin implementation seems to be the best integrated.  Tiger's just a different beast, although it seems to me to share the simple (sometimes to a fault), easy, must work mantra of GNOME, but it implements those goals with much more flare. Best thing to do would be to try it, go to a Mac store and just play around for an hour.

P.S., Mac OS is sort of a throwback to the shareware city that is Windows. You may find that many of the native apps you're interested in are all $10-$25 USD.

---

### Post by DrFunkenstein on 2006-02-27
[QUOTE=ORiON2012]Airport Extreme will not work under Linux, which sucks. [/QUOTE]
Doesn't it work now? At least I'm pretty sure there already are releases for the broadcom drivers, though as I don't have an Airport Extreme I can't comment on this from experience.

As others said, Fink is really quite good and should give you a lot of the software you are used to from Linux.
About running Ubuntu on an ibook. I do this on an older ibook and though it sure isn't without problems (for examples, propietary software that is available for x86, like adobe reader, flash or the ati drivers) aren't available for ppc, it works quite well overall.

---

### Post by newbie2 on 2006-02-27
> A CLAIM by a PC World hack that Apple is about to ditch OS-X in favour of Microsoft Windows has sparked protests and cartoons from the faithful.

John Dvorak quoted Yakov Epstein, a professor of psychology at Rutgers University who said there were four portents indicating this apocalypse was at hand.
[http://www.theinquirer.net/?article=29920](http://www.theinquirer.net/?article=29920)
:rolleyes:

---

### Post by xequence on 2006-02-27
> P.S., Mac OS is sort of a throwback to the shareware city that is Windows. You may find that many of the native apps you're interested in are all $10-$25 USD.

Thats the biggest thing keeping me away from OSX.

---

### Post by eriqk on 2006-02-27
[QUOTE=xequence]> P.S., Mac OS is sort of a throwback to the shareware city that is Windows. You may find that many of the native apps you're interested in are all $10-$25 USD.
Thats the biggest thing keeping me away from OSX.[/QUOTE]

I've found that this situation was actually getting better. There seems to be more and more freeware and free software available for OS X these days. Most of it only supports 10.3 and up, however, which is why it was useless for me at work (where we used 10.2).

Groet, Erik

---

### Post by refdoc on 2006-02-28
I have an ibook (G4 12" since 1 year) and am using it now (>6/12) exclusively under Linux (ubuntu)

OSX does have fink, gentoo-on-mac and a BSD derrived ports collection (Darwinports IIRC). All in all you will find all big Linux software there. You will find not though modern versions - at the time I still explored it gnome was commonly on 2.8 or 2.10 in most distros, while fink gave 2.4 away.

OSX is very slow in comparison to Linux on the same machine. OSX as a GUI sucks. sweet and eye candy on the first look, but then slowly it creeps onto you how utterly useless it is - little in terms of configuration and lack of very simple functionality - mind you in comparison to Win it obviously wins +++.

Airport Extreme worsk absolutely fine under Linux. i am sitting here on my ibook and am connected to a fast WEP encrypted wireless connection. Setting it up was a doodle.

Apple and Broadcom (the chip maker) were more than unhelpful in the wireless matter, but Open Source wins always... :-) Some guys produced a driver, finished  autumn last year,  and it still gets gets better.

The CVS version has WPA working too, but as I do not use WPA at the momentg I have not bothered.

---

