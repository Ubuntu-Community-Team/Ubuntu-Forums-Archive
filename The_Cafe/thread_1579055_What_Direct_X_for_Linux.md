---
title: "What?? Direct X for Linux?"
date: 2010-09-21
forum: The Cafe
---

### Post by JDShu on 2010-09-21
Well, Direct 3D anyway. It looks like some devs are implementing the Direct3D API for Mesa.

Really early stages and I'm somehow pessimistic about it, but its a really cool effort nevertheless.

[http://lists.freedesktop.org/archives/mesa-dev/2010-September/003129.html](http://lists.freedesktop.org/archives/mesa-dev/2010-September/003129.html)

---

### Post by matthewbpt on 2010-09-21
Sounds amazing to me! Direct X games would run much better with wine, and maybe some game developers will start releasing direct x games to Linux (unlikely but possible). Phoronix article [http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1](http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1)

Microsoft must have some patents relating to Direct X, which is potentially dangerous for this project

---

### Post by chris200x9 on 2010-09-21
> **matthewbpt said:**
> Sounds amazing to me! Direct X games would run much better with wine, and maybe some game developers will start releasing direct x games to Linux (unlikely but possible). Phoronix article [http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1](http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1)

Microsoft must have some patents relating to Direct X, which is potentially dangerous for this project

my thread was useless before it even began...oops

---

### Post by undecim on 2010-09-21
Cool. Maybe Regnum will work on this computer soon.

---

### Post by Frogs Hair on 2010-09-21
I found this at gnome look  and thought it may be interest . I have Windows so I don't need it .[http://gnome-look.org/content/show.php/DirectX+10+Ubuntu+Installer+Script?content=129102](http://gnome-look.org/content/show.php/DirectX+10+Ubuntu+Installer+Script?content=129102)

---

### Post by CJ Master on 2010-09-21
> **matthewbpt said:**
> Microsoft must have some patents relating to Direct X, which is potentially dangerous for this project

Bingo.

---

### Post by earthpigg on 2010-09-21
> **matthewbpt said:**
> 
Microsoft must have some patents relating to Direct X, which is potentially dangerous for this project

Only if it is a commercial project intending to do business in the United States.

---

### Post by bigseb on 2010-09-21
A step in the right direction I feel

---

### Post by dirt_diver on 2010-09-21
So when would we be able to use it for gaming?

---

### Post by fatality_uk on 2010-09-21
> **dirt_diver said:**
> So when would we be able to use it for gaming?

Hold your breath, count to 100 in your head and then release.

May still take many months, if not years before anything useful come from this. As for the legal, I'll happily test and should I receive any cease and desist letters from Redmond, they will be filed correctly.

---

### Post by endotherm on 2010-09-21
yeah, it will be patent-encumbered to the hilt, but I'd imagine half the wine implementation is too. 
I'll give it a go

---

### Post by Dustin2128 on 2010-09-21
> **undecim said:**
> Cool. Maybe Regnum will work on this computer soon.
regnum has a linux native client and opengl support...

---

### Post by Slug71 on 2010-09-21
Very interesting.

So with the help of Delta3D or OGRE, would Wine even be needed? Shouldnt it be a lot easier to just port the game over to Linux?

---

### Post by CJ Master on 2010-09-21
> **Slug71 said:**
> So with the help of Delta3D or OGRE, would Wine even be needed? Shouldnt it be a lot easier to just port the game over to Linux?

Well first off, this is going to happen for a long while (if at all,) and I highly doubt it will ever be perfect. Also, not everybody is going to be willing to port, especially for old games/programs.

---

### Post by JDShu on 2010-09-21
> **CJ Master said:**
> Well first off, this is going to happen for a long while (if at all,) and I highly doubt it will ever be perfect. Also, not everybody is going to be willing to port, especially for old games/programs.

While it will take a long while, I have no idea what scale we are looking at. This is primarily a proof of concept project for Gallium and I believe in theory, it should be easy to implement in comparison to what Wine has been doing. To me, "a long time" could be anywhere from 1 year to never.

---

### Post by murderslastcrow on 2010-09-21
In the short term, it will be very beneficial to Wine. As it stands, most Wine users are gamers (or at least, the votes on AppDB tend to indicate this strongly). So, Adobe fans probably won't rejoice, but I'm sure it will get a lot more games playable on our side of things, making Linux more viable for hardcore gamers. Any help at all is good, and Wine still works with the majority of applications, so we've only got.. another 15 years to go? Haha.

Something tells me that, by that time, desktops won't be the standard for computing. After all, they already have an MID/tablet/laptop out that runs three different OSes, depending on its mode. Very ingenious and clever- if it's here now, who's to say this won't be the main method of computing in 10 years? The level of convenience is astounding.

However, if we can play games like HalfLife 2, from that dead Windows generation on a Linux computer with Wine, then heck- why not? Same deal with us playing the original Prince of Persia with DOSBOX today.

However, things are kind of levelling out- I think desktop Linux will still be suitable for a variety of tasks in fifteen years, as I doubt it will die quickly as mobiles become strong.

But yeah, in an ideal world, this implementation of DirectX will see the same motivation and usefulness as Mono, and we'll have people porting their games more easily to Linux by either using straight DirectX, or having a DirectX library referring to OpenGL (kind of like Wine, but backwards).

Either way, this will probably be a good thing in some capacity. Again, just like the Wine project, we'll worry about patents when they've been shown to be an issue with the owners.

Obviously, if a lot of games are ported with this technology, Microsoft will probably have something to say about it.

---

