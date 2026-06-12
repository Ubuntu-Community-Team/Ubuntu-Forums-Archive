---
title: "Gtk + Cairo + Size Change = Corruption"
date: 2009-07-04
forum: Ubuntu Dev Link Forum
---

### Post by sharkbaitbobby2 on 2009-07-04
Hi,
I have an application that can be viewed in full screen.  When it's in full screen, I use Cairo to draw a nice border so it's not too ugly. (See first screenshot.)  But, when the size changes where the border would be extended up and down, the image is corrupted. (See second screenshot.)  Changing back to a smaller size still leaves corruption.
This happens both in full screen and normal size.  In full screen, changing the workspace or exiting and re-entering full screen fixes the corruption.  In normal size, only minimizing and unminimizing the window fixes the corruption.  Hovering over the buttons to force a re-expose doesn't fix it.
This occurs on both Intel graphics with Intrepid's driver and ATI graphics with Jaunty.  It is just a coincidence that it's corrupted for both, or am I doing something wrong somewhere?

[This is the .c file]("http://bazaar.launchpad.net/~memorizer/memorizer/trunk/annotate/head:/src/mem-flash.c"). [Here is a PPA]("https://launchpad.net/~memorizer/+archive/ppa") if you want to try it.

Thanks.

---

### Post by alexmurray on 2009-08-18
Try calling gtk_widget_queue_draw() after disconnecting your expose handler to force the window to get redrawn by gtk

---

### Post by sharkbaitbobby2 on 2009-08-18
I only disconnected the expose handler when it exits fullscreen, and it redraws correctly.  But I tried doing gtk_widget_queue_draw() on the window (the widget "expose-event" is connected to) when the back and forward buttons are clicked, and it works now!  Thanks!

---

