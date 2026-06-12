---
title: "Keystroke overlay display for screencasting?"
date: 2009-02-21
forum: Ubuntu Studio
---

### Post by jeffk on 2009-02-21
I'm evaluating tools for screencasting on Linux (Gentoo ~x86 and Ubuntu 8.10/9.04, specifically).

One of the things I'd like to integrate is a transparent overlay display of keystrokes in human-readable form, to demonstrate keyboard navigation and shortcuts.

Any suggestions on a FOSS tool to do this for Linux? I'd like to use something standalone, available even when not screencasting.

Update: I saw:
[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)
[https://edge.launchpad.net/notify-osd](https://edge.launchpad.net/notify-osd)

which seems like it would be a useful mechanism for keystroke display. However, notify-osd is probably too new to have a utility ready for this specific purpose. It's also important to have positioning capability of the keystroke overlay for less-than-full-screen captures.

Thanks.

---

### Post by Stochastic on 2009-02-21
> **jeffk said:**
> One of the things I'd like to integrate is a transparent overlay display of keystrokes in human-readable form, to demonstrate keyboard navigation and shortcuts.

Why don't you just write into a txt document, turn the opacity down to %30, set the window to "always on top" and move as you please?

---

### Post by jeffk on 2009-02-21
My description wasn't very clear. I'm looking for a FOSS tool to replicate the fancy (e.g. Mac screencasts)  on-screen display of the keystrokes used while interacting with the program being demonstrated.
```
C-x k <return>   ( each line ... fades out ...)
C-x 0 C-x b <right> <return> 
<S-iso-lefttab> <tab> M-> 
<tab> <down> <tab> M-e M-e M-e M-e 
```
It's usually a semi-transparent overlay in a fixed-position on the screen.

Emacs has a way to show this in a buffer, but I would like to do the same for demonstrating browser-base and other GUI apps.

Thanks.

---

### Post by Stochastic on 2009-02-26
Well I've managed to stumble across a differnt notification system (other than the ubuntu-specific and yet to be released notify-OSD).  I don't know if it has a tool like what you're looking for, but...

Mumbles - [http://www.mumbles-project.org/](http://www.mumbles-project.org/)

Possibly take that and combine it with something like keyboardcast: [https://launchpad.net/keyboardcast](https://launchpad.net/keyboardcast) or Xmacro: [http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/) to get your desired results?

---

### Post by jeffk on 2009-02-28
Thanks for the tip, Mumbles looks like something I would like to build upon, I'll investigate.

The new notify-osd looks great, but I think the conventions they are wisely placing upon its notifications will make its formatting less than optimal for keystroke-echoing during screencasts.

In the parallel thread on Gentoo, a reply and I found python-xlib, which makes sane keystroke event watching possible. The challenge would be to group and expire the keystrokes in such a way that they resemble input intent, such as emacs chords, etc.

[http://python-xlib.sourceforge.net/](http://python-xlib.sourceforge.net/)

I'm sure I've seen this feature on the best-produced screencasts, strange that I can pin down its colloquial name from commercial (i.e. Mac) packages.

Thanks.

---

### Post by Ubuntiac on 2009-06-15
Hey, I just found a near perfect solution!

Go to [http://screencasters.heathenx.org/blog/2009/04/06/smaller-key-status-monitor/](http://screencasters.heathenx.org/blog/2009/04/06/smaller-key-status-monitor/) and download the archive.

Run it with sudo python key-status-hx

and you get a perfect small onscreen widget thing that shows keys and mouse button presses. You can remove the window decoration in Kubuntu by right clicking the window titlebar and choosing Advanced _> no border. I imagine Gnome / XFCE is similar.

Happy screencasting!

---

### Post by mathfeel on 2010-10-15
> **Ubuntiac said:**
> Hey, I just found a near perfect solution!

Go to [http://screencasters.heathenx.org/blog/2009/04/06/smaller-key-status-monitor/](http://screencasters.heathenx.org/blog/2009/04/06/smaller-key-status-monitor/) and download the archive.

Run it with sudo python key-status-hx

and you get a perfect small onscreen widget thing that shows keys and mouse button presses. You can remove the window decoration in Kubuntu by right clicking the window titlebar and choosing Advanced _> no border. I imagine Gnome / XFCE is similar.

Happy screencasting!

I come across this thread when I am searching to do the same thing. This script looks interesting, but it depends on HAL, which are no longer used in newer version of X.

---

### Post by lpanebr on 2011-03-31
Just found this which seems great and supports the windows meta key!

[http://code.google.com/p/key-mon/](http://code.google.com/p/key-mon/)

Luciano

---

### Post by twinoatl on 2012-07-06
[screenkey]("http://pabloseminario.com/projects/screenkey/") is great and compatible with current Ubuntu release

---

### Post by marinara on 2012-07-08
screenkey is  compatible, if by "comatible" you mean buggy and abandoned.  I can't get the preferences dialog to show

---

### Post by wildmanne39 on 2012-07-08
Old thread closed.

---

