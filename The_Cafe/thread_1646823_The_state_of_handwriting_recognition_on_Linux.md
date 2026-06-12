---
title: "The state of handwriting recognition on Linux"
date: 2010-12-16
forum: The Cafe
---

### Post by ssalman on 2010-12-16
Recently I bought a second hand tablet computer to experiment with thinking that it would make a great living room computer for quick tasks while setting at a couch; I first considered iPad but it's not exactly a personal computer, plus I love having a Linux tablet handy. I was pleased to see all hardware worked OTB with Ubuntu 10.10, including the Wacom pen digitizer.
 
However, I was taken back with the feature gap between Windows and Linux when it comes to handwriting recognition. I spent a couple of days searching the internet for open source handwriting recognition and came up with virtually nothing that compares to Windows offering. Still, I found [Cellwriter ]("http://risujin.org/cellwriter/")which is great handwriting character recognition software, and its sure handy, but is not a natural handwriting recognition software by design as it recognizes characters not words. I came across [STIHRS]("http://stihrs.sourceforge.net/") which seemed to be neglected. I also came across [Zinnia ]("http://zinnia.sourceforge.net/")library, but couldn't find a GUI application written for it.[
 
I know that Cononical is developing a new desktop environment called Unity that is planned for Ubuntu 11.04 and emphasizes touch UI, but I didn't find anything to speak of handwriting recognition features. I used to think that Linux can out perform other OSs when it comes to functionality, not polish (although the polish gap has been decreasing over the years). But I now believe I may have stumbled on an area where it may not hold true. Maybe this is what an R&D budget like Microsoft's brings to computer users; it's been developing this for the past 15 years. 
 
What do you think? And do you know of any current development efforts that address this gap?

---

### Post by Favux on 2010-12-16
You are correct and handwriting recognition is sadly lacking in Linux.  CellWriter is currently the best on offer, and it is pretty good.

The best offered was an Evernote demo on their website for linux, but they took that down 2-3 years ago.  The next best was Xstroke, but that hasn't been developed for 4-5 years.  There are a few others out there but also basically non-functional.

However there are now 3, I think, active OCR projects that have lately sprung up or become more active.  It's possible that an engine they come up with can be parleyed into handwriting recognition.

---

### Post by ssalman on 2010-12-17
[FONT=Calibri][SIZE=3]Favux – I'm Glad you stopped by and commented here, as I would like to thank you for all your efforts in writing guidelines for setting up tablets and helping others setup their tablets on this forum. I've used many of your helpful comments to setup rotation scripts and other things on my tablet, so THANKS![/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]To your point, I too noticed that there are few OCR projects active with some of them including handwriting code but deactivated at the time being such as [ocropus]("http://www.ocropus.org/")[/SIZE][SIZE=3].[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Now I did find a very intresting solution to utilize Windows handwriting recognition capabilities under Linux (see [here]("http://ubuntuforums.org/showthread.php?t=1147022")[/SIZE][SIZE=3]). I'm going to give it a try later this winter break to see how it works, if it works as well as it is reported, that certainly can buy me time until a native solution is developed for Linux.[/SIZE][/FONT]
 
[COLOR=black][FONT=Calibri][SIZE=3]In the mean time, any chance we can recommend this as a future Ubuntu project?[/SIZE][/FONT][/COLOR]
 
[FONT=Calibri][SIZE=3]Thanks for your input.[/SIZE][/FONT]

---

### Post by samalex on 2010-12-17
To be honest, how many geeks have hand writing that's even legible to themselves :)  I know my handwriting is HORRIBLE because I type everything, and unless I type my notes from meetings directly afterwords I might as well not have written anything because a week later I won't have a clue what I wrote.

Seriously, I think they need to offer hand writing classes in college because I think writing has started to become a lost trait.

---

### Post by Favux on 2010-12-17
Hi ssalman,

In the short term if someone picked up Xstroke I don't think it would take too much to get it going on current versions of the Xserver.  I know a Ubuntu dev. did that a while ago for the then Ubuntu release.  Depends on whether the Xstroke developer would give permission I suppose.  I think his algorithm looks reasonably fast.

Then you could see someone integrating it into Xournal (plug in?).  Maybe look at what CellWriter is using for recognition.  Throw in a predictive dictionary and possibly a neural net layer and you might have something.  Call it LinX Note?  It wouldn't be as accurate as what you see with Microsoft or whatever but it might be good enough.  Until a true recognition engine was developed for linux.


Hi samalex,

lol  That's why I print everything now a days.  Pretty fast at it too.

---

### Post by NCLI on 2010-12-17
> **samalex said:**
> To be honest, how many geeks have hand writing that's even legible to themselves :)  I know my handwriting is HORRIBLE because I type everything, and unless I type my notes from meetings directly afterwords I might as well not have written anything because a week later I won't have a clue what I wrote.

Seriously, I think they need to offer hand writing classes in college because I think writing has started to become a lost trait.
Why bother? It's dying out for a reason.

---

### Post by BigSilly on 2010-12-17
> **NCLI said:**
> Why bother? It's dying out for a reason.

Because we're all too goddamn lazy to put any effort into anything these days? :D

---

### Post by bcw on 2011-05-22
I released a new [solution]("http://ubuntuforums.org/showthread.php?t=1733298") which is easier to set up.

Cheers,
bcw

---

