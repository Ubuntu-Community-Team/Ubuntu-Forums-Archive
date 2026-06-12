---
title: "scrollbar scrolls by itself when mouse is moved"
date: 2013-08-14
forum: System76 Support
---

### Post by system76panp9 on 2013-08-14
I am running Ubuntu 13.04 and using a Pangolin laptop with a
touchpad and the touchpad is disabled for clicking on it and for
two finger scrolling also

what is happening is that the vertical scrollbar on various
applications is scrolling all by itself unpredictably when I use
the touchpad to move the mouse cursor, even if the cursor is
nowhere near the scrollbar or trough or buttons and even if
I am not holding down any button for dragging

for instance, I open a page in Firefox and the mouse is up in
the address bar area where I have just typed in the URL

I use the touchpad to move the mouse cursor down into the
page to click on a link, not holding down any buttons, and the
cursor is at least three inches from the scrollbar on the right
side of the page, nevertheless the scrollbar scrolls the page up
about an inch as I am moving the cursor

I guess I am just wondering if anyone else has had this
problem, and if there is any chance it is something that
could be correctable in software or if it seems to be definitely
a hardware issue

thanks for any guidance

---

### Post by Y^2om&amp;#7sgP on 2013-08-15
Hi system76panp9

never had this problem on Linux of any flavour, but have on a number of occasions on Windows (I'm a techie for a company that only uses M$ :mad:

I find that more often or not it's a hardware issue.

Have you tried cleaning the touchpad?

It may also be worth booting from a live cd to see if the problem persists, that'd confirm or disprove the hardware theory :)

---

### Post by isantop on 2013-08-15
Is it possible you're accidentally brushing the touchpad with a second finger? Ubuntu has inertial scrolling where content will coast after scrolling quickly, and if you brush the trackpad briefly, it may still be coasting when the cursor moves down into the scrollable content.

---

### Post by system76panp9 on 2013-09-12
I am not brushing the touchpad with a second finger, anyway as I said I have got 2-finger scrolling
setting disabled so I do not think that would be relevant? re: inertial scrolling, I have seen some other
posts talking about some kind of virtual driver for touchpad called "evdev" that has one setting which
apparently could be responsible for the behavior I am seeing, it is a setting that lets a user scroll
without holding down any mouse buttons, which is exactly what is happening randomly to me, however
it is not the default setting for "evdev" so I cannot imagine how it would have gotten set that way
and anyway I cannot find any "evdev" driver on my system ... maybe there is a corresponding System76
custom driver that somehow can be set to do the same thing, that is, allow scrolls without any
buttons being pushed? I wonder if it could be something in GTK since they monkeyed around with
the scrollbar behavior for the Gnome 3.6 update without documenting what they did particularly well?
it is incredibly annoying so I am pretty desperate, any help would be greatly appreciated

---

