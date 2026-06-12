---
title: "Is Windows Font Rendering Fixable?"
date: 2013-07-30
forum: Windows
---

### Post by buzzingrobot on 2013-07-30
Anyone know how to make Windows font rendering something less than abysmal?

I haven't been near Windows for years.  But, recently I've been helping a friend with her office hardware running Windows 7 and her laptop with Windows 8.  The fonts look awfully shabby on both. 

We've found lots of online advice claiming to improve Windows font rendering.  None really worked. Cleartype is tweaked, font smoothing is on, the displays are at their native resolution and DPI, and yet the pixellation is obvious.

Is this fixable, or is my friend stuck with fuzzy fonts?

---

### Post by papibe on 2013-07-30
Hi buzzingrobot.

The easiest way is to install the Ubuntu restricted extras packages, that includes the Microsoft fonts.

For that take a look at this: [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

If you only would like to install **only** the fonts, take a look at this other: [Microsoft Fonts]("https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts").

Let us know how it goes.
Regards.

---

### Post by buzzingrobot on 2013-07-30
My question is about font rendering on Windows, not Windows fonts on Ubuntu.

---

### Post by speartip on 2013-07-31
Not sure what you can do, but if you have any luck please post back.
I have been triple booting ubuntu/kubuntu/windows 7. And everytime I have to log into Windows, I'm always amazed at how poor the fonts look.
I have tried all kinds of things with no success, and so now live with it.

---

### Post by buzzingrobot on 2013-07-31
> **speartip said:**
> ... everytime I have to log into Windows, I'm always amazed at how poor the fonts look.

I spent a lot of time over the weekend on this. Nothing I tried delivered any real improvement.  I learned that Windows uses at least 3 different techniques to render fonts. Many apps have not been upgraded to use newer techniques that might deliver a better display. 

ClearType is Microsoft's version of subpixel rendering, which does improve rendering on LCD's. That improvement is small, though, compared to Ubuntu. The fonts look the same as they did when I gave up on Windows about 10 years ago.

ClearType is not available for the new Metro interface in Windows 8, so the web is littered with complaints about ugly Win8 fonts.

Some people do think Ubuntu fonts are fuzzy and prefer Windows-style rendering.  I don't disbelieve them.  We all have different eyes.  But, Ubuntu fonts look solid and distinct to me, with no fuzziness.  Meanwhile, Windows fonts seem spindly and thin to me, pixellated and with stringy gray artifacts inside characters like "O" and "e" and often trailing off large headline-sized characters.

---

### Post by Rebelli0us on 2013-08-05
People complain about Windows fonts being too thin. Is that it?  Otherwise it may be a video driver problem.

---

### Post by buzzingrobot on 2013-08-05
> **Rebelli0us said:**
> People complain about Windows fonts being too thin. Is that it?  Otherwise it may be a video driver problem.

While I'd say the fonts are thin, thinness does not preclude legibility.  It's legibility that's the problem. For instance:

-- Large bold headline characters, say, 60px black, that should have solidly distinct straight edges -- like "E" and "B" -- often do not.  For lack of a better phrase, the edges can appear as if painted by a sloppy painter who left behind faint brush strokes "outside the lines".

-- Headline-size characters sometime have very thin gray edges.

-- Sometimes these large bold headline characters have thin strings of gray pixels curling away from them.

-- Curves in large characters are visibly step laddered.

-- Text sized for ordinary reading seems pixellated. I.e., viewed closely, individual pixels are apparent. Viewed at a normal distance, they look spindy and mis-shapen. 

-- The space inside closed loops in ordinary text -- in an "o" or a "b" -- often is not empty, but, instead, shows pixel-sized spots of gray. This is not the "fuzz" some see on heavily anti-aliased letters.  These spots are floating inside the loop.  They are not attached to the letter.

The equipment is reasonably high end -- it's a pro photography business -- and the faults are visible on machines with different video cards and monitors,   ruling those out as the cause. There is an OS X machine in the mix whose fonts do not exhibit these faults when I attached one of the monitors used on a Windows machine.

In addition, the symptoms are essentially the same on Win7 and Win8. (I'm aware that Win8 has reverted to grayscale antialiasing for Modern apps, which I would not expect to look good on anything less than a high DPI display.  Unfortunately, I believe no desktop monitor on the market is high DPI.  They all cluster in the 96-110 range, with one or two outliers hitting 130.)

It's a pity, because Win8, once I found a way to avoid the Modern bits, has some attractive capabilities that might persuade me to use it at home, if not for the font rendering weaknesses.

---

### Post by bcschmerker on 2013-08-06
I run an Asus® CM1630-06 under Microsoft® Windows® Se7en™ Service Pack 1 64-bit 7.0.8001 (MultiProcessor Kernel 6.1.7601) with a Hewlett-Packard® HP2009m fluorescent-backlit LCD display unit.  Here's what I found concerning Advanced System Settings -> Visual Effects:

1.  Depending on your default screen-text and icon-label font, "Smooth edges of screen fonts" may be either needed or undesirable.
2.  Deselecting "Use drop shadows for icon labels on the desktop" and "Show shadows under windows" can mitigate artifacts on certain fonts.

ClearType can be calibrated for accurate subpixel rendering on LCD's; I undertake that when necessary as part of routine maintenance.

---

### Post by buzzingrobot on 2013-08-06
Thanks, we'll try that drop shadow fix. Turning off font smoothing  is a no go.  Adjusting Cleartype makes what I'd call marginal changes, but none of the alternatives presented by the Cleartype tuner are particularly attractive. They're all rather consistently jaggy. Cleartype has no affect on the Modern (aka Metro) interface and apps in Win8 nor in that release's IE.

I know this is a complicated issue because Windows supports several rendering techniques to maintain compatibility with old code. So a fix that works for one application may not work for another. It seems odd to me that Microsoft hasn't addressed this or that the Windows community has not cobbled together some kind of workaround.  

One recurring response I've seen on Windows forums is that Microsoft isn't going to address this because they expect the problem to be ameliorated by high-DPI displays.  However, there are no high-DPI desktop displays on the market and panel makers seem uninterested in making them given the scale of the phone and tablet market.

---

### Post by nicolas.br4cq on 2013-12-17
Searching on Google and I found this Google Code Project : [https://code.google.com/p/mactype/](https://code.google.com/p/mactype/).
It's a little software which can manage fond rendering on Windows (see more detailed preview here : [http://superuser.com/a/627689/282602](http://superuser.com/a/627689/282602)).

After trying the software, I'm really satisfied and I recommend it.

---

