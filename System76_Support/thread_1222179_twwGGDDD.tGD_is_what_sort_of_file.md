---
title: "twwGGDDD.tGD is what sort of file?????"
date: 2009-07-24
forum: System76 Support
---

### Post by bill516 on 2009-07-24
I am running Ubuntu 8.10 on a Pangolin PanP4.  Good system, no problems.  Yup, I would buy localetc's machine if I needed another one.

Very odd situation.

I saw 3 items in trash and tried to empty trash.  No luck.  Usually this is some sort of permission problem.  No luck manipulating permissions.

There are three of these files.  They are fairly large, 1.1 to 2.1 Gigabytes for a total of approx 4.3 Gigabytes.

Their very peculiar names are:

DDDDHDaD.DaD  (Note in this file the lower-case "a" in both places carries an umlaut.  Swedish?  German?

DtGDDHtD.HDD

twwGGDDD.tGD

I have never seen anything remotely like this.  A Google search on these names produced nothing at all, which is almost unprecedented in my experience.  Google usually come up with something.

Does anybody have any clue what these things are?  Short of physical violence (probably not a good idea!) how do I get them off my machine?

OK Tom, just a little magic ..........

---

### Post by philcamlin on 2009-07-24
maybe they are virtualmachine drives or something because of .hdd

---

### Post by thomasaaron on 2009-07-24
If you navigate to the trash directory and try to remove them with...

sudo rm <filename>

...but tab out the filename instead of trying to spell it out, maybe it will work. It could be that tabbing it out will account for the foreign characters, whereas spelling it out may not.

Peculiar, indeed.

---

### Post by bill516 on 2009-07-25
Thanks to you, Tom & Phil.  Phil, you remind me that I did briefly experiment with virtual machines a while back.  I noticed the "HDD" but really did not know what to make of it.

Tom, I'll try your technique.  It really would be a shame to nuke such a nice little machine!

I must travel for the next few days.  But I will report back and let you know how this worked.

---

### Post by bill516 on 2009-07-25
Tom, your technique worked.  So I will edit that first post and mark this solved.  I really think Phil nailed it.  I'd bet this stuff is left over from some experimentation I was doing with Virtual Box.

---

