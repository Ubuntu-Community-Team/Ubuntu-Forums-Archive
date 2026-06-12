---
title: "[Idea] Enable Open Office Optimize Output"
date: 2007-12-08
forum: Ubuntu Brainstorm
---

### Post by LavianoTS386 on 2007-12-08
I noticed that if you go to Tools>Options>View and check OpenGL, Optimized input, and I believe Hardware Acceleration, as well as, automatic resize of toolbar icons, which arn't enabled by default, the load time decreases and views better on devices with smaller displays.

---

### Post by Lster on 2007-12-08
Well I had a little play around and I timed the opening of OpenOffice.org.

This is how long it took with "OpenGL" and "Optimized output" enabled:
> real    0m0.768s
user    0m0.004s
sys     0m0.004s


And this is how long it took with them unchecked:
> real    0m0.790s
user    0m0.000s
sys     0m0.000s


As you can see, I had very little difference in opening times. And these results don't _appear_ to be consistent when I try more times: sometimes one is faster than the other (to open). There could be a slight improvement, but it doesn't look like much...

I think, maybe those options improve performance for other things (perhaps graphics?).

---

### Post by LavianoTS386 on 2007-12-08
^ Did you try those one after the other, or did you restart your computer after the first try? I's been my experience that Open Office load faster the 2nd time you load it, regardless.

---

### Post by Lster on 2007-12-09
For each setting I changed I closed Open Office and started it up once, before testing it. I'll now try rebooting in between openings.

Here is Open Office after a reboot with the "OpenGL" and "Optimise output" settings checked:

> real    0m8.605s
user    0m0.000s
sys     0m0.004s


And without:

> real    0m8.404s
user    0m0.004s
sys     0m0.008s


I was launching Open Office Writer both times after rebooting. I tried to wait roughly the same time after logging in to open Open Office, but I don't know how fair I was. I did try to wait until there was no hard disk access...

But these tests are only really significant to me. If your computer loads Open Office faster with those options enabled, then maybe it will for some others? You could perform your own benchmark to check how fast it really is?

---

### Post by LavianoTS386 on 2007-12-09
Do you have instructions on how?

---

### Post by Lster on 2007-12-10
See Wikipedia about the Unix time command.

[http://en.wikipedia.org/wiki/Time_%28Unix%29](http://en.wikipedia.org/wiki/Time_%28Unix%29)

---

