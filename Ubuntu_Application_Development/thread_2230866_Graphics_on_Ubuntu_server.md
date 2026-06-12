---
title: "Graphics on Ubuntu server"
date: 2014-06-21
forum: Ubuntu Application Development
---

### Post by bob40 on 2014-06-21
Okay, I am looking to write a program for Ubuntu in C.  I have a lot to learn, but have done enough programing that I think I can get it figured out eventually.

The problem I am having now is figuring out where to get started with graphics.  My needs will be very basic, some buttons a graph and such.  I have found Cairo and read enough tutorials to understand the basics and get started with ONE exception.  I don't know how to render the image to the screen.  I saw how to create a line, box, text and so on, but could not figure out how to make my surface the computer screen.  I want to take over the whole screen with my program until I exit.  I do not want to use Ubuntu desktop.  Can anyone point me in the right direction?

I have searched for hours, but only find how to use (in non specific terms) cairo, or how to render in a window on the desktop version.

Thanks,
Bob

---

### Post by tgalati4 on 2014-06-22
Normally, you would install the X-Windows server (xorg) and that handles the graphics--that is the purpose for a graphics server.  Otherwise you have to write your own, and you won't find many tutorials on how to do that in linux.  I would install the desktop version and learn to use the extensive graphics frameworks that already exist.  Is this for an embedded platform that can't run the desktop version?  If so, there are tiny versions available like tinycore linux.

---

### Post by bob40 on 2014-06-22
It is eventually for a rasberry pi.  Memory is a BIG consideration  Also my grahpic needs are simple.  I just need some basic shapes, some text and some lines.

Bob

---

### Post by bob40 on 2014-06-26
Is there really no way to do graphics without a desktop?

---

### Post by steeldriver on 2014-06-26
... I've never done it, but I think the concept you're looking for is a [framebuffer device]("http://en.wikipedia.org/wiki/Linux_framebuffer") (unless you can manage with just a text/table-based interface, in which case ncurses would probably be the way to go)

---

