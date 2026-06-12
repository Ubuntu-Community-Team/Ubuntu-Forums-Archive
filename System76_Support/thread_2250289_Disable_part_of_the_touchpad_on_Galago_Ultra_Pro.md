---
title: "Disable part of the touchpad on Galago Ultra Pro"
date: 2014-10-27
forum: System76 Support
---

### Post by vitoshka on 2014-10-27
The touchpad on Galago UltraPro is huge and is not centered with respect to the editing part of the keyboard. So my palm is always moving or pressing the mouse while typing. 

The common two solution that could be found on the forums are either to play with disabling the touchpad on typing or enabling palm detection. This could be done with GUI settings or with 

```
syndaemon -i 2 -t -K -d
```.

None of the above worked well for me, so I have ended up with the third solution. I have disabled the right strip of the touchpad like this:

```
synclient AreaRightEdge=5000

```

Hope it's helpful to other people as well.

---

