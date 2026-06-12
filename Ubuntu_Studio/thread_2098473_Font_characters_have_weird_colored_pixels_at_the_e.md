---
title: "Font characters have weird colored pixels at the edges"
date: 2012-12-26
forum: Ubuntu Studio
---

### Post by blenderkid on 2012-12-26
Hi,

I've installed Ubuntu Studio 12.04. The installation was flawless and everything seems to work, but as the title says... All the characters have colored pixels at the edges.

There is no problem with icons or images, those are displayed normally.

I was told, there must be a problem with xorg, but I don't know anything about how to xorg modification...

I hope someone knows how to fix this.. It is really exhausting to read as it is now...

Thank you very much in advance,
blenderkid

---

### Post by blenderkid on 2012-12-26
I've found the solution, it was a problem of font antialiasing. I had to turn off the color setting.

---

### Post by mwinthrop on 2012-12-26
It might be the way anti-aliasing is set up on your system.  If you are using Ubuntu Studio 12.04 with XFCE, try opening up "Appearance"under the "Settings Manager" and adjusting the anti-aliasing "Hinting," "Sub-Pixel Order", or just disabling anti-aliasing outright.  You could also try finding a webpage displaying various anti-aliasing settings and try to optimize this setting.  I saw a web page likes this once, but can't remember where it is anymore.

Edit - see you found the solution already.

---

