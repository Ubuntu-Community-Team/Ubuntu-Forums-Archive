---
title: "Trying To Use A Tablet!"
date: 2009-05-03
forum: Wine
---

### Post by OrangesAndCoffee on 2009-05-03
Hi guys, I'm new here and recently switched to Ubuntu (Loving it!). I still have to use some window applications however and one of which is Pen Power Junior (Version 7 I believe) I can install the program just fine but when I try to open it (And access the USB tablet) it tells me it cannot run its recognition system (So no tablet). Is this a problem with wine or is it something to do with a lack of additional settings?

The program is unicode and windows based, if that information helps.

Thanks in advance!

---

### Post by cogadh on 2009-05-04
It's probably because the app relies on some Windows driver to work, which are not present (and wouldn't run anyway) in Wine.

---

### Post by NightMKoder on 2009-05-04
Doesn't look like its even on wine's appdb. There's probably absolutely no chance it will work (tablet apps dont like wine too much). First make sure that your tablet works outside of wine, then try again.

If that fails, I suggest looking for an alternative (I'm sure there is one).

---

### Post by asdfoo on 2009-05-04
Which version of Wine are you using?  Try upgrading to 1.1.20 [http://winehq.org/download](http://winehq.org/download)

---

### Post by OrangesAndCoffee on 2009-05-04
I'd figure as much that it needed something from windows.

I got the most recent Wine version.

Is there any alternative I have in terms of emulating that driver perhaps?

---

### Post by asdfoo on 2009-05-04
> **OrangesAndCoffee said:**
> I'd figure as much that it needed something from windows.

I got the most recent Wine version.

Is there any alternative I have in terms of emulating that driver perhaps?

well, my intuos works fine in Wine apps, if the app just uses the windows ap for tablets then it shouldn't need an additional driver other than the linux one, do you have that installed?

which tablet do you have?

---

### Post by OrangesAndCoffee on 2009-05-04
Pen Power Junior v.7.0 It says on the back M/N: Touch pad PD4UA.

Its chinese based for the most part, and writing the name for it without the tablet of course limits my ability to provide speciifcs.

But the literal translation of it is "small stylus pen".

I'm thinking of installing XP on a small parition for wine-incapable programs, but I'm trying to avoid it.

---

### Post by Favux on 2009-05-04
Hi OrangesAndCoffee,

I don't know if this will help (I doubt it) but I helped someone setup their PenPower tablet a few weeks ago using the linuxwacom version of the Wacom drivers in Intrepid.  We seemed to have got it mostly working when he switched to Jaunty.  In Jaunty he ran into the linuxwacom problems they've been having.  So I don't know if we could have finished setting it up.

---

### Post by OrangesAndCoffee on 2009-05-04
Thanks for the information!

I'll look into it, it might actually work.

My limited understanding on the driver it uses is that more than likely that windows has a general driver for all tablets, which have their own recognition software.

I'll try using Wacom's linux software and see if it works, I'll report on it if there's any results.

Thanks again!

---

