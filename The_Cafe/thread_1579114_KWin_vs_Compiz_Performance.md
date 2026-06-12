---
title: "KWin vs Compiz Performance"
date: 2010-09-21
forum: The Cafe
---

### Post by beastrace91 on 2010-09-21
Maybe this is another reason for me to start using KDE again... Recently [ran some tests]("http://jeffhoogland.blogspot.com/2010/09/are-your-desktop-effects-slowing-you.html") and found that Compiz slows down 3D performance by about 10%, while KWin on the other hand only slows performance by only 1%

I like having my flashy effects enabled always... Guess it is time to hop back on the KDE bandwagon.

~Jeff

---

### Post by Half-Left on 2010-09-21
Were these tests performed with 'Unredirect Fullscreen Windows' on using Compiz?

---

### Post by FuturePilot on 2010-09-21
That will probably change when you upgrade to 10.10 as the version of Kwin in 10.10 uses OpenGL.

---

### Post by beastrace91 on 2010-09-21
> **Half-Left said:**
> Were these tests performed with 'Unredirect Fullscreen Windows' on using Compiz?

Only if it is turned on by default.

~Jeff

---

### Post by beastrace91 on 2010-09-21
> **FuturePilot said:**
> That will probably change when you upgrade to 10.10 as the version of Kwin in 10.10 uses OpenGL.

Who said anything about using Ubuntu? :P Is this just 10.10 or something new with KDE 4.5.x?

~Jeff

---

### Post by FuturePilot on 2010-09-21
> **beastrace91 said:**
> who said anything about using ubuntu? :p is this just 10.10 or something new with kde 4.5.x?

~jeff

kde 4.5

---

### Post by Tibuda on 2010-09-21
> **beastrace91 said:**
> Only if it is turned on by default.

~Jeff

it is off by default

---

### Post by SmSpillaz on 2010-09-22
It simply isn't possible to get accurate performance and slowdown numbers when running compositors and OpenGL applications, simply because there are too many factors involved, see this blogpost: [http://smspillaz.wordpress.com/2010/05/21/beware-the-benchmarks/](http://smspillaz.wordpress.com/2010/05/21/beware-the-benchmarks/)

In reality, it should be possible to optimise the process of surface-binding for openGL applications in the future, especially now that we have GEM/TTM and various bits and pieces in the nvidia driver.

Currently, the binding process is multi-faceted:
application -> opengl -> buffer -> pixmap -> texture -> compositor-> buffer.

Steps 4 and 5 are essentially redundant and also expensive, since there is an expensive memory copy operation from graphics memory -> server memory -> graphics memory.

It would be better if we could use framebuffer objects from those applications directly and use them to render-to-texture. Unfortunately there is no unified framework to do this, really. (Such an approach would have very very little slowdown).

---

### Post by Water_Spirit on 2010-09-22
> **FuturePilot said:**
> That will probably change when you upgrade to 10.10 as the version of Kwin in 10.10 uses OpenGL.

The version of Kwin in my 10.04 is using OpenGL now.

---

### Post by forrestcupp on 2010-09-22
> **beastrace91 said:**
> Only if it is turned on by default.

~Jeff

Try it again with that turned on and tell us your results.

---

### Post by beastrace91 on 2010-09-22
> Unredirect Fullscreen Windows

What exactly does that do and if it *should* help performance why isn't it enabled by default? I'll try and re-run the benchmarks with this later this week or next.

~Jeff

---

### Post by FuturePilot on 2010-09-22
> **beastrace91 said:**
> What exactly does that do and if it *should* help performance why isn't it enabled by default? I'll try and re-run the benchmarks with this later this week or next.

~Jeff

It draws fullscreen windows directly to the screen instead of to the offscreen buffer. Basically it bypasses the compositor.

---

