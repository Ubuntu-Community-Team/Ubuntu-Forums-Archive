---
title: "What's new in the Gazp9? And graphics optimization question"
date: 2013-09-18
forum: System76 Support
---

### Post by haroldtwilkins on 2013-09-18
Hey guys, extremely satisfied Gazelle Pro8 user here! I saw that the new Gazp9 is out, what are some of the big new features? I saw what looked like a usb 3.0 port next to the headphone jack, along with a slightly newer processor and graphics chip. Anything major that I'm missing out on?


Also I game from time to time on TF2/CSS, anybody have any tips for optimizing graphics performance? I get around 40fps on lowest settings.

Thanks!

---

### Post by rorschachwalter on 2013-09-18
You're not missing out on anything really, no. I suppose someone could mention the new microphone placement (by the webcam, where any capable designer would place it), or the fact that the touchpad is actually clearly distinct from the chassis (what a novel concept!), or the fact that the mouse has two distinct buttons (another novel concept!). But other than that, it's basically the same thing. Speakers, build, etc, are all as you'd expect from the previous model, unfortunately.

As for performance, are you asking about the GazP8 or the GazP9? Either way, you could upgrade to kernel 3.10 and mesa 9.2. This should, in theory, improve graphics performance by a bit (more if you're using Haswell), although in my experience installing these actually leads to worse performance and a number of bugs being introduced on Haswell. If you're getting a solid 40FPS, you're getting better than I was getting with the GazP9's HD 4600. Certain things, like engineer buildings, dropped the framerate significantly. And dropping settings to low didn't improve things any noticeable amount. The biggest performance boost was dropping from native to a lower resolution, but even then, it wasn't a big boost, and dropping to the lowest resolution didn't improve things any further.

So basically, the integrated chip on Linux drivers doesn't perform too well. It does better on Windows. But if you can upgrade safely to a solid 3.10 kernel and mesa 9.2, you should get *some* improvement.

---

