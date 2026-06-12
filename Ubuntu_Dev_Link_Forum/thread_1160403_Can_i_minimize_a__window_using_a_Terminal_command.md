---
title: "Can i minimize a  window using a Terminal command ?"
date: 2009-05-15
forum: Ubuntu Dev Link Forum
---

### Post by barantamer on 2009-05-15
Hello ,
I want to  minimize or close a window using a terminal command . Is this possible ?

---

### Post by stroyan on 2009-05-15
The xwit command that is part of the xwit package will do that.
The tricky part is identifying which window you want to effect.
The default for xwit uses the WINDOWID environment variable.
That is often set by terminal emulators.
But 'xwit -iconify' under a gnome-terminal's shell won't iconify it.
That is because the WINDOWID set by gnome-terminal is a sub-window of the top-level window that iconify could work with.
It would be possible, but not simple, to find the right top window of a gnome terminal by use of xwininfo and xprop commands.
Another approach would be to select the window by window name.
But that name may not be a unique attribute of the one window you want.

---

### Post by alseambusher on 2012-12-29
Use this script: [https://gist.github.com/4408536](https://gist.github.com/4408536)
or follow this post
[http://lifepluslinux.blogspot.in/2012/12/minmising-window-in-gnome-354.html](http://lifepluslinux.blogspot.in/2012/12/minmising-window-in-gnome-354.html)

---

