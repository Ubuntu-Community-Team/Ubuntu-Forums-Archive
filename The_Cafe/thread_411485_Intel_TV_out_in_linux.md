---
title: "Intel TV out in linux?"
date: 2007-04-16
forum: The Cafe
---

### Post by PatrickMay16 on 2007-04-16
Hello people.

I recently obtained a laptop. Now, this laptop has an intel video device, and it has an s-video out connector. Does anyone else have a laptop with an intel video device and TV out? Does it work for you, or is the TV out not supported in linux?

Just making sure before I buy a s-video to composite converter.

---

### Post by chalimac on 2007-04-17
I think the package you need is i855-crt. But I can't confirm this.

---

### Post by Biochem on 2007-04-17
Works great for me. Also have a look at this post.
[http://ubuntuforums.org/showthread.php?t=361124&highlight=dual+monitor](http://ubuntuforums.org/showthread.php?t=361124&highlight=dual+monitor)

---

### Post by legolas558 on 2009-09-21
Pushed by frustration of having to close my Linux sessions and boot into
Windows, I packaged a chroot live system to use my TV-OUT without rebooting.
Xorg 1.4 + the old i810 driver (v1.7.2) are inside, with perfectly compiling
sources.

I hope this will be useful to some of you.

[http://sourceforge.net/projects/i810tvout/](http://sourceforge.net/projects/i810tvout/)

All feedback is welcome (on the SF.net project please)

---

