---
title: "avi to dvd - why so involved?"
date: 2010-02-11
forum: Ubuntu Studio
---

### Post by rdh61 on 2010-02-11
Hi,

I wanted to escape completely from the dreaded Windows, but there is just one little thing stopping me...

I've been trying to do (in Ubuntu) what I feel should be a very simple thing for a long time without success: to turn avi files into a viewable dvd.

I've tried devede and brasero, k3b, tovid and others. They're all involved, very long, and end in error messages and wasted blank dvds.

 I don't want optimum quality, I want simplicity, speed and I want it to work. I've read the theory that that's too much to ask, it's a complicated process, there are technical limitations etc. etc.

I don't buy this explanation though, as in Windows I can just drop three avi files into DivX Player, hit "burn" and I have my viewable dvd in 5 minutes. So easy.

So I'm curious - what is the problem in developing something like this for linux. Or perhaps somebody actually knows something like this for linux?

Thanks for any comments.

---

### Post by LuridCinema on 2010-02-11
DVDstyler... all you would do is setup the DVD for NTSC or PAL and drag the AVI file onto the program.. add a button to the menu to start play, indicate the button will play all titles add a pic for the menu and hit burn. Select the drive and you will have a DVD

There are how to videos on Youtube for DVD styler

---

### Post by rdh61 on 2010-02-11
Thanks for that. I'll try it and then feed back.

---

### Post by rdh61 on 2010-02-25
OK, I finally got round to it. Well, (unlike all the others) it works, which is the main thing. But (like all the others) the process is very long (hours).

Can any techno wizards out there answer this simple question: how is it that DivX Player (on Windows) can do this job (no frills, just basic viewing quality - what I want) in literally 5 minutes, yet nobody has been able to develop a similar tool for linux?

---

### Post by gordintoronto on 2010-02-25
How long is your video? How fast is your computer?

I have used devede and it worked just fine, the first time I tried it.  It took about 1.5 times the viewing time of the video, on a 3 GHz AMD X2 processor.

Does Divx Player actually produce a normal DVD, or does it just burn the AVI as a data file?  If that's all you want to do, Brasero is all you need, and it will take a couple of minutes.

---

### Post by rdh61 on 2010-02-25
118 minutes viewing time, Intel Pentium 4, 3GHz processor.

Yeah, DVDStyler took about the same amount of time as you get from devede (which I could never get to work).

DivX Player produces viewable DVDs of comparable length in little over 5 minutes.

---

### Post by chewearn on 2010-02-25
For 5 minutes burn of 110 minutes video, DivX player is clearly not doing any transcoding.  That means it's creating a data disc.

The default disc burning utility should be able to do that. Simply drag-drop the file into CD/DVD creator window (launched from the Places menu).

---

### Post by rdh61 on 2010-03-02
> **chewearn said:**
> For 5 minutes burn of 110 minutes video, DivX player is clearly not doing any transcoding.  That means it's creating a data disc.


Thanks. Yes, having explored the discs created, that may well be the case. Thing is, I can pop it in the DVD player and it plays, and is complete with menu. Isn't that all that's necessary? So why all the transcoding?!
Anyway, if you're right, thanks, that simple observation will save me angst! Still have to try out a data disc burned with Brasero though. Will let you know.

---

### Post by chewearn on 2010-03-02
> **rdh61 said:**
> Thanks. Yes, having explored the discs created, that may well be the case. Thing is, I can pop it in the DVD player and it plays, and is complete with menu. Isn't that all that's necessary? So why all the transcoding?! 

For a set-top DVD player to be able to play avi, divx, etc files dropped into a data disc, the player needs to be DivX certified and support reading data disc and decoding of the files.

On top of that, a set-top DVD player might or might not support different physical disc format: e.g. CD-R/W, DVD+R/W, DVD-R/W.

In other words, features of a set-top DVD players can vary a lot.  The lowest common denominator is DVD-Video format, which is compulsory (if you want the DVD logo on the player).  Everything else is optional add-on for the player manufacturer.

So, I supposed the standard encoding to DVD-Video format is adopted by these creator software to ensure 100% compatibility.

Except DivX player software, of course.  DivX gets a percentage royalty for each DVD player sold with the "DivX certified" logo, so naturally, they want to push adoption of their format.

> Anyway, if you're right, thanks, that simple observation will save me angst! Still have to try out a data disc burned with Brasero though. Will let you know.

Good luck!

---

