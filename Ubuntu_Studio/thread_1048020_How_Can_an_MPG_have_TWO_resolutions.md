---
title: "How Can an MPG have TWO resolutions?"
date: 2009-01-23
forum: Ubuntu Studio
---

### Post by HalNineThousand on 2009-01-23
I've got some .mts files that I converted to .mp4 files, then viewed them in Kaffeine.  I picked "Track Info" from the menu.  The resolution is reported as:

1920 x 1080
(1440 x 1080)

Then when I used FFmpeg to convert them to use on DVDs, I played the .mpg file and picked "Track Info" and got:

853 x 480
(720 x 480)

So what's the deal?  Is one the "actual" resolution and the other an apparent resolution because the pixels are rectangular and not square?  (That's my best guess.)

Why do I get two resolutions reported?

Thanks for any insight on this.

---

### Post by FakeOutdoorsman on 2009-01-23
Aspect ratios are confusing.  The [Aspect Ratios](http://www.doom9.org/index.html?/aspectratios.htm) article at doom9.net may help clear things up.

---

### Post by HalNineThousand on 2009-01-24
Big help, Thanks!

Basically confirmed what I thought but included some details that helped.

---

