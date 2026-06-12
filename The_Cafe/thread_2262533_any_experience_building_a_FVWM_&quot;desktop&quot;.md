---
title: "any experience building a FVWM &quot;desktop&quot;?"
date: 2015-01-25
forum: The Cafe
---

### Post by nep-nori on 2015-01-25
So I'm always trying to make the most of my toaster (read: PC) and so I've been compulsively downscaling my desktop environment periodically. Last thing I did was build a custom DE using the Ubuntu 14.04.1 LTS netboot mini.iso as the base and adding strictly what I need in the form of a stripped down Xubuntu (basically just XFCE4 components added one by one, not the actual Xubuntu).

Having said that, recently someone pointed me towards window-managers such as openbox, fluxbox, icewm and the incredibly pretty yet still lightweight fvwm and its cousin fvwm-crystal. I've been reading about these options but openbox is by far the most well-documented with more than a few full-fledged tutorials out there.

Long story short, **¿does anyone run FVWM and/or FVWM-Crystal or know of a good tutorial on how to build it up into a DE from a "clean" Ubuntu minimal install?**
(this is actually a not-subtle-at-all way for me to request a tutorial)

Here's a little more on the subject:

"FVWM-Crystal is a theme framework for the FVWM window manager. It uses GUI  tools to edit the look of windows, instead of the use of editing a text  file in FVWM. It creates a desktop environment using FVWM as its window  manager and main core. It features flexible window decorations, and a file manager may be optionally used to display desktop icons; ROX-Filer, Thunar and Nautilus are supported for this task. FVWM-Crystal offers user interface integration for some terminal emulators like xterm, aterm and rxvt-unicode, for a tray system such as stalonetray or trayer-org, for various music players - among them Audacious, MPD, Quod-Libet, XMMS and XMMS2 - and for the video/audio player MPlayer,  to the point where it can control these components. FVWM-Crystal makes  use of semi-transparency. Almost everything on the default desktop is  semi-transparent." ~from Wikipedia's article [http://en.wikipedia.org/wiki/FVWM-Crystal](http://en.wikipedia.org/wiki/FVWM-Crystal)

That is perfect for me btw, as I prefer Thunar as my file manager, xterm for my terminal emulator, Audacious for my FLACs and MPV (successor of MPlayer2) for my vids.

Here are some videos too:
(the board wouldn't allow me to embed all 3)

[video=youtube;A3ZAKJeXKdc]http://www.youtube.com/watch?v=A3ZAKJeXKdc[/video]

[http://www.youtube.com/watch?v=IxxEBA3uXFQ](http://www.youtube.com/watch?v=IxxEBA3uXFQ)

[http://www.youtube.com/watch?v=9bMSeGgw_Eg](http://www.youtube.com/watch?v=9bMSeGgw_Eg)

FVWM-Crystal's website: [http://fvwm-crystal.sourceforge.net/](http://fvwm-crystal.sourceforge.net/)

FVWM's website: [URL="http://fvwm.org/"]http://fvwm.org/
[/URL]
on a completely unrelated note, coffeecat's an alright guy (or gal).

---

### Post by d-cosner on 2015-01-25
Some years ago I installed and configured FVWM but I added it to PCLinuxOS if I remember right. It took a lot of searching even then to get it all how I wanted it. I remember it was extremely light! I had it installed on a Pentium 166 MMS with 32 MB of RAM.

I can see where you could use some guidance because of how you are wanting to build this. Sounds like a minimal Xfce base would be the best place to start since you specifically want Thunar as the file manager. The stripped dow Xubuntu you mentioned sounds like a good starting point, then add FVWM and go from there. Configuring menus is pretty straightforward once you see how the entries are created.

As I remember FVWM Crystal was what I had and I was able to make it look and work well, it just took some Google searches and patience to get it done.

---

### Post by nep-nori on 2015-01-26
Well, I've been doing some googling and I came across a FVWM forum [where I made a thread similar to this one]("http://www.fvwmforums.org/phpBB3/viewtopic.php?f=6&t=3064") but activity there is significantly lower than in here.

---

### Post by kevdog on 2015-01-27
Nice video above showing some of the basic things about the window manager.  Don't know too much about fvwm, although I've used openbox, fluxbox, and enlightenment before.  Wish the enlightenment party would get its act together since by far that was my favorite light weight window manager.  Thanks for video.  Now why cant the Mac people learn something about how windows receive their focus and raise and lower -- Geez!!!

---

### Post by nep-nori on 2015-01-27
since I started looking into FVWM I've discovered quite a bit of great alternatives to apps, but I'll post those if/when I have a good list of packages for my custom Ubuntu; and if there's any interest at all.

In the mean time, there's another fork of FVWM called FVWM-Nightshade (FNS), here's its website: [http://fvwm-nightshade.github.io/Fvwm-Nightshade/](http://fvwm-nightshade.github.io/Fvwm-Nightshade/)

---

