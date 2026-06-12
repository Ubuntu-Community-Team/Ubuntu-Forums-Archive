---
title: "Xgl, Xegl, Xglx, AIGLX, Compiz, Beryl......"
date: 2006-11-14
forum: The Cafe
---

### Post by timbobsteve on 2006-11-14
Hi All,

Just trying to do some reading about developments in X technology and came across a few 100 terms that confuse the hell out of me. I thought I would post here and see if anyone can clarify them for me.

As far as I can tell AIGLX and Xgl are two different approaches at the same problem, hardware accelerated X servers.

Xegl and Xglx are both early implimentations of the Xgl idea, but Xglx is being used while people wait for Xegl to be finished and still requires a running standard X server to work, whereas Xegl is a completely rewritten X server based on DRI and Direct Framebuffer (directfb) technology.

AIGLX as far as I can tell is a project with identical goals to Xgl, but started from scratch because the Xgl design specs were created away from the community behind closed doors. AIGLX members felt that this introduced a bunch of problems in using it as the new standard and set out to create their own truly-open spec for Accelerated X Server.

As far as I can tell Compiz and Beryl, at this stage, are very similar and provide window management and have sub-programs to handle decorations+effects.

As far as I can tell both Xgl and AIGLX both require Binary Drivers to run properly (is this correct?).

```

(Xgl)

Xglx --> Compiz / Beryl --> Window Decorations = Cool Graphics

(AIGLX)

AIGLX --> Compiz --> Window Decorations = Cool Graphics


```

Now... is that right or have I got things all wrong? Just wanted to know this stuff for future reference. Also, what do people think of in general about replacing Xorg / XFree86? I personaly think that a custom written X Server with 3D Acceleration is a step in the right direction, if only to keep up with modern hardware. Also I think alot of cool features could come  out of a accelerated desktop (things like Expose from Apple's OS X) to really improve usability.

Thanks.

-Timbobsteve

---

### Post by 23meg on 2006-11-14
> As far as I can tell both Xgl and AIGLX both require Binary Drivers to run properly (is this correct?).Not necessarily; Intel provides open source drivers for their chips with the required support, for example. 
> Now... is that right or have I got things all wrong?See the part titled "Stacking the blocks" in [this article]("http://jonsmirl.googlepages.com/graphics.html"), which is a comprehensive insider's review of things going on.> lAso, what do people think of in general about replacing Xorg / XFree86? I personaly think that a custom written X Server with 3D Acceleration is a step in the right direction, if only to keep up with modern hardware.I'm all for keeping the current X.org; a separate server has many disadvantages and little benefit, especially with hardware.> Also I think alot of cool features could come out of a accelerated desktop (things like Expose from Apple's OS X) to really improve usability.
Ditto, already happening with Beryl.

---

