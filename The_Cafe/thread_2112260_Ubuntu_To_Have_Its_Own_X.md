---
title: "Ubuntu To Have Its Own X ??"
date: 2013-02-04
forum: The Cafe
---

### Post by jpaulb on 2013-02-04
There's been talk already this morning in [the forums]("http://phoronix.com/forums/showthread.php?77327-239-News-Stories-amp-20-Articles-About-Linux-This-Month&p=310670#post310670"),  Twitter, and via email to Phoronix that Canonical is allegedly  developing its own display server rather than using X.Org/X11 or  Wayland.

[http://www.phoronix.com/scan.php?page=news_item&px=MTI5MjI](http://www.phoronix.com/scan.php?page=news_item&px=MTI5MjI)

---

### Post by 3rdalbum on 2013-02-04
It took the Wayland guys years to go from zero lines of code, to a server that ships with no desktop distros except Rebecca Black Linux.

Maybe Canonical has written its own display server for the phone, but I think it's probably years away from being useful on the desktop.

I know that they seem confused about who will use Ubuntu Phone, why anyone should buy it, and even about what features it will and won't have; but recently somebody from the project said that apps not written in QML will still run. I doubt the Ubuntu devs have ported every toolkit to run on their own display server, so my guess is that the display server is still X, but a more simple implementation of it.

---

### Post by mips on 2013-02-04
They are free to do as they please. Adoption by others might not go down so well though.

---

### Post by mamamia88 on 2013-02-04
I read that article on omgubuntu.   Ok x is old. But it works.   It would be much easier to fix problems with x then to re invent the wheel imo.

---

### Post by forrestcupp on 2013-02-04
> **mamamia88 said:**
> I read that article on omgubuntu.   Ok x is old. But it works.   It would be much easier to fix problems with x then to re invent the wheel imo.
I agree. Wouldn't this pretty much break everything?

---

### Post by mamamia88 on 2013-02-04
> **forrestcupp said:**
> I agree. Wouldn't this pretty much break everything?

Not if done well. But why throw away work that has been done for 30 years?  They are free to do whatever they want.  But, I think their resources would be better off spent contributing to existing projects and differentiating themselves from other distros in other ways like creating applications that are better then what's out there. For example apple differentiates themselves by providing a suite of high quality apps with every mac. I think they are on the right track with stuff like the dash and Ubuntu one I think they should focus on more stuff like that that provide users with features they would miss if they switch distros.

---

### Post by grahammechanical on 2013-02-04
Ubuntu is already making use of Android display technology in Ubuntu for Android. Canonical will use whatever open source solutions it can to bring about the goal of making Ubuntu a multi-device platform. The focus over the last few years has shifted away from Ubuntu on the desktop. At present the development focus is on Ubuntu on mobile devices.

Improvements will filter down to Ubuntu desktop but I do not expect great changes to the display server for the simple reason it would be a diversion from making Ubuntu a multi-device platform.

Regards.

---

### Post by Jakin on 2013-02-04
I sure would be nice to get many of the issues with xorg fixed. I would have to say xorg is the main thing that ends up breaking my system eventually.

---

### Post by BrokenKingpin on 2013-02-05
Hmmm... not sure how I feel about it. It might be necessary for them to do this to support the phone stuff they are doing. I just don't like them deviating so far from the standard Linux desktop technologies. The more they do that, the more I want to move to another distro. I just don't want to be locked into Ubuntu specific stuff... starting to feel like Apple, which is not a good thing for me.

I think the problem with xorg is the fundamental design, which you cannot just fix. Once in a while you just have to throw it away and start on something better from the ground up. Sure, this will be extremely painful in the beginning, but better in the long run.

My money is on Wayland, as it will have wider support from all the distros.

---

