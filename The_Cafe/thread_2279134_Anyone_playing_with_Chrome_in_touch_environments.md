---
title: "Anyone playing with Chrome in touch environments?"
date: 2015-05-21
forum: The Cafe
---

### Post by Copper Bezel on 2015-05-21
My main machine is an Asus X202 out of the Vivobook line, and it has a multitouch screen. I've not really used it extensively - the machine came with Windows 8, but at the time, Ubuntu had a small problem with the touchscreen events getting "stuck" such that single-tap stopped registering, and of course Ubuntu has always had better multitouch trackpad implementation than Windows, so switching the machine to Ubuntu was a funny trade-off, that the touchscreen worked less but the touchpad worked more. And then Chrome had this terribly strange behavior with tearing off tabs, that if I did it by a touch drag, it'd get "stuck" to the pointer and nothing I could do would "let go".... 

It's all sorted now - the touchscreen works reliably, including Touchégg gestures to bring up the window spread or launcher and so on. 

Chrome still has this odd little bug that causes it not to always recognize that there's a touch interface present, and I'd looked up the workaround for it, but in the process, ran through about:flags again to make sure I hadn't accidentally broken it myself. Anyway, I ran into an option for overlay scrollbars. They work quite a lot like Ubuntu's, but interestingly, also work with touch (touching the region expands the handle, and then it can be dragged on screen like any scrollbar could.) I really rather like the flick gestures for back and forward, too.

Just curious whether anyone else has played with any of this, etc. I imagine the behavior is all very similar to Chrome on Chromebooks or Windows 8 PCs with touch. Just kinda neat. = )

---

### Post by Kpenguin on 2015-05-22
Are you talking of Chrome OS, or Chrome Browser? Ubuntu definitely needs better touchscreen drivers and integration.

---

### Post by Copper Bezel on 2015-05-23
The Linux build of Chrome browser, as in the proprietary blend of Chromium, as in the base of the app that's used in Chrome OS on top of Google's core GNU-Linux blend, although I know they differ slightly. In any case, I'm running ordinary Chrome in ordinary Ubuntu 14.04 with Unity and playing with the touch interaction thereof. 

And it ... sorta works. Some touch features do, some don't. I get a special, Android-esque selection marquee in text boxes, with the little handles at the ends and a menu that says "paste" and "...", when I tap into a text field - but none of those things work. = / Dragging to select seems to trigger the Back and Forward gestures instead. It wouldn't really work on a device that had the touchscreen as the only pointing device, but the features that do work are handy. 

On the Ubuntu side of touch support things, touch drivers are working smoothly and predictably now on my X202. I can even pinch zoom in Chrome. It's nice. Desktop Unity isn't very touch friendly, what with all the tiny controls and things like the launcher autohide not using the phone's edge swipe for touch and so on, but Unity in 14.04 isn't meant for touch environments even as much as the Gnome 3.12 (or is it 3.10?) it's built on already is. Obviously, that's not the case with Unity Next or whatever, since it's supposed to share with the phone version.

Edit:

Have to make a correction in my vague reference to Gnome being more touch ready, although I don't know if this is an Ubuntu thing.... I hadn't actually *used *Gnome Shell in some time, and I'm finding it bafflingly less touch-friendly than Unity despite being designed around touch-friendly elements. I've found that the unified tootlebar thing responds to touch "clicks," but not dragging on the handle area, so I can't move windows around with touch if they use client-side decs. And the Shell behavior is a little strange, too - the status area, clock, and application menu respond to taps, but the elements *inside *don't, and indeed can't even be *clicked* if I open the menus using touch - except when I have the Overview open, where they respond normally. Very strange.

---

