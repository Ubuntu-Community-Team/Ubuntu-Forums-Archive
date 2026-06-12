---
title: "Strange Touchpad behavior on Gazelle"
date: 2009-07-23
forum: System76 Support
---

### Post by darkknight045 on 2009-07-23
Since installing Jaunty I've been experiencing some strange touch pad behavior on my GazP5.

Essentially the scrolling feature is working in an incredibly bizarre way:

if I run my finger along the right edge, it does -nothing-, going along the bottom edge engages the horizontal scrolling.

If I have 1 finger on the touchpad and start sliding with a second finger it will start doing the vertical scroll, but its incredibly temperamental and erratic.

Disabling the scrolling feature does not impact this behavior.

---

### Post by thomasaaron on 2009-07-23
Yep. That's the new default behavior. It is pretty silly, though, IMHO.

---

### Post by jdb on 2009-07-23
> **darkknight045 said:**
> Since installing Jaunty I've been experiencing some strange touch pad behavior on my GazP5.

Essentially the scrolling feature is working in an incredibly bizarre way:

if I run my finger along the right edge, it does -nothing-, going along the bottom edge engages the horizontal scrolling.

If I have 1 finger on the touchpad and start sliding with a second finger it will start doing the vertical scroll, but its incredibly temperamental and erratic.

Disabling the scrolling feature does not impact this behavior.

If you slide both fingers the vertical scroll works a lot better.

jdb

---

### Post by darkknight045 on 2009-07-23
> **thomasaaron said:**
> Yep. That's the new default behavior. It is pretty silly, though, IMHO.

Ugh....agreed.

> **jdb said:**
> If you slide both fingers the vertical scroll works a lot better.

jdb

Interesting, I will try this when I get home tonight.

---

### Post by rumblered on 2009-07-24
I've always loved and wanted two-finger scrolling and am happy to now have it. You get the whole touchpad for cursor movement instead of having an invisible line past which the behavior changes.

Though it will catch people off-guard who don't know about the change. It expects both fingers to roughly line up horizontally across the touchpad. If you put your fingers out vertically or too crooked, the scrolling will be pretty erratic.

---

### Post by drewbenn on 2009-07-25
If you don't like the new way of scrolling, you can try reverting to the old behavior:
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```
If you want to make it permanent across power cycles:
```
echo "options psmouse proto=imps" | sudo tee -a /etc/modprobe.d/options.conf
```
I am much happier since I reverted to the old method! :)

---

