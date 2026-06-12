---
title: "Extra spacing between glyphs for monospace fonts"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-03-27
Even with a dual head setup, for me, screen real-estate is a premium commodity.

My particular font preference was for DejaVu Sans Mono 8 (which with Pango was actually 10.666).
I even went so far as to patch emacs23 for oneiric ([https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/931849](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/931849)) so that I could use the 10.666 fractional pixel sizes (which was visually equivalent to using gedit/gnome-terminal with Monospace 8 as the system fixed font).

What's unique about fractional pixelsize in monospace fonts is that the glyphs can be "sized up" while keeping the metrics tight. This gives a somewhat similar appearance to variable-width fonts.

I was a little disappointed with all the extra space between monospace-font glyphs in Precise.

At first, I thought it would be something simple like the Xft dpi setting had been muffed. No such luck. Unfortunately, where fonts are concerned there are a number of actors and they're all complicated. However, after several hours of digging, I have found the offending change introduced in FreeType upstream, and submitted the bug and patch together ([https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/966654](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/966654)).

For those of you that like space between the glyphs -- you're all set. Those of you that would like it to be as it was, the quilt patch is straightforward.

---

