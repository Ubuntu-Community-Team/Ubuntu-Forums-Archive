---
title: "Daily Images for Raring - Get yours here"
date: 2012-11-07
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2012-11-07
The Raring Ringtail daily images are starting to appear here:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds]("http://iso.qa.ubuntu.com/qatracker/milestones/243/builds")

There is now an image for Desktop amd64 without the +mac. No fries either, I suppose. :(

There is also the beginnings of an official Cadence testing schedule (in contrast to my attempt at a planner) here:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring]("https://wiki.ubuntu.com/QATeam/Cadence/Raring")

It was last edited on 6th November. Lets see how it goes.

**Update**

Just tested the 20121107 desktop amd64 image. It is dangerous. Well, almost. The live session is fine but installing with is bad.

I did not get an Allocate Drive Space screen. So, there was no Do Something Else option. It went to Location, Keyboard, Who Are you? And then the slide screen. That works great. Thankfully nothing else happened. It did not install. There was not any transfer of files. I do not want to risk another attempt to install in case it uses the entire disk without asking.

Did they forget to include Ubiquity in the image?


Regards.

---

### Post by ventrical on 2012-11-07
@grahammechanical

  I am just wondering if there is some duplicity here at the testers wiki?

[https://wiki.ubuntu.com/U+1/tester-wiki](https://wiki.ubuntu.com/U+1/tester-wiki)

---

### Post by grahammechanical on 2012-11-07
Duplicity or duplication? The two words have the same origin but this side of the pond 'duplicity' is not a nice thing to do.

A little bit of duplication I think. Harmless? Yes.

---

### Post by ventrical on 2012-11-07
> **grahammechanical said:**
> Duplicity or duplication? The two words have the same origin but this side of the pond 'duplicity' is not a nice thing to do.

A little bit of duplication I think. Harmless? Yes.


I should have use redundancy instead. Harmless ? Of course it is. I have this conservative bent at times. Waste not , want not?  :) . I am not trying to be pernikity here. lol

Regards..

---

### Post by kaldor on 2012-11-07
For those new to testing Ubuntu development releases, this little script I made may be of use to ease the process: [http://ubuntuone.com/48C4m1xAfoX2Lo88oDeUQR](http://ubuntuone.com/48C4m1xAfoX2Lo88oDeUQR)

It asks which version of the ISO you want (32 bit, 64 bit, ARM), syncs it (rsync), and offers to create a live USB (unetbootin) or live DVD.

---

### Post by mc4man on 2012-11-07
> **grahammechanical said:**
> 
Did they forget to include Ubiquity in the image?
Regards.
No it's there.
A guess may be that some of the .py scripts that should run aren't, maybe because of the change to python 3.3 or whatever it is now.

---

### Post by smartboyhw on 2012-11-08
> **mc4man said:**
> No it's there.
A guess may be that some of the .py scripts that should run aren't, maybe because of the change to python 3.3 or whatever it is now.
Yes you are correct.

News freshly delivered from #ubuntu-release.

This actually has a bug.

Number: LP #1076305
Title: plat-x86_64-linux-gnu is still incomplete
Targeted packages: python-3.3 (Raring), ubiquity (Raring)
Reporter: xnox

Hmm I shall wait then until this gets fixed.

---

### Post by mc4man on 2012-11-08
> This bug was fixed in the package ubiquity - 2.13.1

---------------
ubiquity (2.13.1) raring; urgency=low

  * Remove dead code in ubi-prepare which breaks with Python 3.3
    (LP: #1076305).
 -- Colin Watson <cjwatson@ubuntu.com> Thu, 08 Nov 2012 10:52:11 +0000

Should be good to go soon 
(or if one as an image could try booting to live session & updating before install

---

### Post by sgage on 2012-11-08
I booted the iso into Live mode, updated ubiquity, and it worked normally. Installing now...

---

