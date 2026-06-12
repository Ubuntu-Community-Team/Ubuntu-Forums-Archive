---
title: "has AMD finally made a driver for my graphics card?"
date: 2010-11-14
forum: The Cafe
---

### Post by mr clark25 on 2010-11-14
i think i finally found a driver for my radeon X1300 pro graphics card [here]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")!

the site looks official, so i'm downloading the file right now. 


does anyone have any warnings for me before i try to install it?

EDIT: reading the release notes, and it says ubuntu is supported. i should probably read the rest of the release notes before i get started...

---

### Post by Decatf on 2010-11-14
Those are old drivers. Don't hold out for anything from AMD. Support was dropped for that card over a year ago. The open source drivers right now are better than those driver ever were.

---

### Post by mr clark25 on 2010-11-14
> **Decatf said:**
> Those are old drivers. Don't hold out for anything from AMD. Support was dropped for that card over a year ago. The open source drivers right now are better than those driver ever were.

they have GOT to be better than the one i'm using. (i never installed one because there was none to install...)

---

### Post by handy on 2010-11-14
Have a look at the OP here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

You need to use the FOSS Radeon driver stack.

---

### Post by mr clark25 on 2010-11-14
> **handy said:**
> Have a look at the OP here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

You need to use the FOSS Radeon driver stack.

i amy not be looking hard enough, but i cant find my card anywhere there....    (or in the links)

got done reading the release notes and such, and it looks like it should be simple to install the drive i mention my OP.

---

### Post by Decatf on 2010-11-14
Don't bother with the drivers in your OP. They won't work with Lucid and will only cause more problems. If you're not convinced enough then look under system requirements in the release notes. It supports up to Xorg 7.4. Lucid has 7.5. The last release of Ubuntu that these drivers supported was 9.04.

The open source drivers which come default with Ubuntu and are the same drivers you are likely usig right now. Follow the steps under **Ubuntu Stuff** in the link that handy posted. You will get more updated drivers from it.

---

### Post by handy on 2010-11-14
> **mr clark25 said:**
> i amy not be looking hard enough, but i cant find my card anywhere there....    (or in the links)

got done reading the release notes and such, and it looks like it should be simple to install the drive i mention my OP.

These links were available via the page I linked to:

This one helps you determine which GPU you have;-

[http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7](http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7)

This one tells you where the FOSS development is up to for the various AMD GPU's;-

[http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7](http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7)

Yours 1300, is supported by the FOSS Radeon drivers.

---

### Post by mr clark25 on 2010-11-14
> **handy said:**
> These links were available via the page I linked to:

This one helps you determine which GPU you have;-

[http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7](http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7)

This one tells you where the FOSS development is up to for the various AMD GPU's;-

[http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7](http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7)

Yours 1300, is supported by the FOSS Radeon drivers.

ok, thanks! i will look into that tomorrow. (its getting a little late here...)

i'm glad i posted before i tried to install it.


also, if it makes a difference, i am running ubuntu 9.10 on the computer that has this card in it. (i think ubuntu 9.10 was a beautiful release, and i will probably stay with it until support for it ends)


so, ill be back tomorrow sometime to try the FOSS drivers. thanks for the advise.

---

### Post by handy on 2010-11-15
> **mr clark25 said:**
> 
...
also, if it makes a difference, i am running ubuntu 9.10 on the computer that has this card in it. (i think ubuntu 9.10 was a beautiful release, and i will probably stay with it until support for it ends) ...

You will still have to use the FOSS driver stack.

---

### Post by Mark Phelps on 2010-11-15
What apparently is not being made clear to you is that you already HAVE the open source drivers installed!  Ubuntu installs them automatically during initial setup. 

There are NO AMD-provided drivers that you can install that will work with your card and current versions of Ubuntu -- period.

So basically, you have nothing to do at this point.  IF you try to force the install of the drivers you downloaded, you will only trash your display, and you'll have to boot into a command line to remove those drivers -- and replace them with the same ones you already have in place!

---

### Post by mr clark25 on 2010-11-15
> **Mark Phelps said:**
> What apparently is not being made clear to you is that you already HAVE the open source drivers installed!  Ubuntu installs them automatically during initial setup. 

There are NO AMD-provided drivers that you can install that will work with your card and current versions of Ubuntu -- period.

So basically, you have nothing to do at this point.  IF you try to force the install of the drivers you downloaded, you will only trash your display, and you'll have to boot into a command line to remove those drivers -- and replace them with the same ones you already have in place!


so, should i try to install the FOSS driver(s), or just stick with what i have? 

right now, gaming performance is lacking. i have a (older) computer with onboard graphics that gets better gaming performance.

---

### Post by handy on 2010-11-15
With Ubuntu it seems you have the current stable FOSS drivers installed by default.

The X1300 graphics card is not a very good gamer, & having a lower powered computer won't help matters any either.

It may help you to appreciate that the X1300 was bought out as a low end card in October 2005.

---

### Post by Mark Phelps on 2010-11-16
> **mr clark25 said:**
> so, should i try to install the FOSS driver(s), or just stick with what i have? 

IF you're running a relatively current version of Ubuntu (9.x, 10.x), then you already HAVE the FOSS drivers installed.  Is THIS clear enough now?

---

