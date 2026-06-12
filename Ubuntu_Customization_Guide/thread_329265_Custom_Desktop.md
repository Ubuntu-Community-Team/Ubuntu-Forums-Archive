---
title: "Custom Desktop"
date: 2007-01-01
forum: Ubuntu Customization Guide
---

### Post by motlive on 2007-01-01
I want to modify Ubuntu desktop to look completely different, remove a lot of the options into hidden menus and change the general desktop enviroment.

Anywhere I should look? tools, guides etc?

---

### Post by _simon_ on 2007-01-01
Edit: Found it :)

[http://www.ubuntuforums.org/showthread.php?t=77694](http://www.ubuntuforums.org/showthread.php?t=77694)

---

### Post by motlive on 2007-01-01
Cheers pal :)

---

### Post by AgenT on 2007-01-01
You are using the GNOME desktop environment, probably the least configurable desktop on Linux. Two things you need to understand. There are mutliple layers to what windows people think of as "desktop". There is the X server (xorg), then there is the [window manager]("http://en.wikipedia.org/wiki/Window_manager") (you use metacity) and then on top of all that, there is the [desktop environment]("http://en.wikipedia.org/wiki/Desktop_environment") (GNOME).

For what you need, you do not have to worry about xorg. The window manager (WM) is the first thing you can change. The WM controls how windows behave. This may not sound like much, but it is. See [Beryl]("http://www.beryl-project.org/") for example (3d wm with a lot of fancy and useful features). There are a LOT of WMs available.

There are not too many DEs available. The reason is, a DE is more or less nothing more than a collection of programs that look at function in a similar way and that work together. 

To configure advanced options in GNOME, you need to use the gconf-editor. Basically, GNOME developers thought it wise to create something like a windows registry. gconf-editor enables you to change entries in this registry. Type gconf-editor in a terminal.

You can always try using a different DE or not use a DE at all. Another popular DE is KDE. In the Ubuntu world, it is called Kubuntu. You can just install the package kubuntu-desktop to have KDE on your system. You can have more than one DE and WM installed, but you can only use one at a time.

There are a LOT of choices on Linux which can be a little confusing if not daunting. However, this same choice gives you so much potential to customize your desktop that it will make your head spin and make those propriatery operating systems look like they never offered any customization in the first place. Windows users get excited when they change a theme or a "shell" which adds "amazing" features like different panel or curved corners.

This brings the last point: you mention wanting to customize your menus and such. In GNOME, just right-click on the main menu icon in the status bar and select "edit menu". Do note that you can also replace only your panel to something else because the panel is nothing more than a program. Before you go crazy on changing your DE or your WM, first look into changing the "small" things like panels or editing your current panel menu system as mentioned above.

Well, this is probably way too much information for you. Good luck with your  customizing. And remember, whatever you though was customization before, it's nothing compared to what you are able to do on Linux.

---

### Post by motlive on 2007-01-01
again, cheers pal, both links very helpful and just what I am looking for. 

my aim is to recreate the 360 dashboard.... only much much better :D

---

### Post by motlive on 2007-01-01
Thanks AgenT, thats helped me understand the system more and what I can do, now to just do it :D

---

### Post by AgenT on 2007-01-01
> **motlive said:**
> 360 dashboardWhat is that? Is it something similar to the OSX dashboard? Can you provide a few links for more information?

---

### Post by motlive on 2007-01-01
its the Xbox 360 DashBoard, here are a few screen shots

[IMG]http://images.betanews.com/albums/6/38.jpg[/IMG]

[IMG]http://files.xboxic.com/general/xbox-360-dashboard/spring-update/xboxscreen008.jpg[/IMG]

im not looking to do a direct rip off, but you can see there is no actual "desktop", just large, what i can only describe as, quick launch icons and links.

---

### Post by AgenT on 2007-01-01
Are you trying to create a [PVR]("http://en.wikipedia.org/wiki/Digital_video_recorder")? Maybe a Kiosk?

Why do you want your desktop to look like an XBox?

Also, to make it a little more clear: if you just want to change how things look (which it looks like you do not), you should just stick with the current WM and change its look via themes. If you wish to change how things function, change the WM. Changing the DE is a little bit of both, changing the function and look. Changing the WM will also change how things look, but a WMs purpose is to change how windows are managed.

A few short example movies of different WMs in action:
[Enlightenment]("http://video.google.com/videoplay?docid=-8555069095815277896") (WM [link]("http://www.enlightenment.org"))
[Beryl]("http://video.google.com/videoplay?docid=-2155353011707841108&hl=en") (WM [link]("http://www.beryl-project.org/"))
Those are not the best videos, but give you some idea of the differences that changing a WM can make.

---

### Post by motlive on 2007-01-02
Well I dont want it to look like Xbox, because lets face it.. its crap :D

but i do want to have it function on a similar level to Xbox..... 

but now that i have seen enlightenment I dont think I will, and ill hack around the stuff I dont want to be visible and remove it from the GUI (somehow).

Its not for a PVR either, just an idea that i have.

---

### Post by AgenT on 2007-01-02
[How To Install Enlightenment E17 The Easy Way]("http://www.ubuntuforums.org/showthread.php?p=1948186")

A few other WMs:
[Metisse]("http://www.youtube.com/watch?v=AT89IOci5FA") (WM [link]("http://insitu.lri.fr/metisse/") - note: not very usable atm)
[FVWM-Crystal]("http://fvwm-crystal.org/user-screenshots/nemo.jpg") & [FVWM-Crystal]("http://polishlinux.org/reviews/fvwm-crystal/fvwm_crystal_top_down.png") (these are images) (WM [link]("http://fvwm-crystal.org/screenshots.html"))
[WindowMaker]("http://jk.yazzy.org/screenshots/windowmaker/wm7.jpg") & [WindowMaker]("http://www.fi.muni.cz/%7Exliska/img/windowmaker-linux.jpg") (images) (WM [link]("http://www.windowmaker.info/"))

And do remember that screenshots or even videos do not show off a WM. You just have to try it. And some WMs (FVWM) are extremely configurable which also usually means they require the user to do some, or a lot, of configuration. Good luck.

---

### Post by motlive on 2007-01-02
Cheers for this, will be installing it tonight and having a play.

still looking at that video has blown me away, absolutely amazing... M$ Suck more than ever now, and i knew they sucked when 98SE got released.

---

### Post by AgenT on 2007-01-02
> **motlive said:**
> Cheers for this, will be installing it tonight and having a play.

still looking at that video has blown me away, absolutely amazing... M$ Suck more than ever now, and i knew they sucked when 98SE got released.
Are we still talking about E? (E = Enlightenment)

What is more amazing is the system specifications. It requires about the same system as Windows 98. It seriously works on a 300mhz computer without any problems. Of course, what programs you use is something else because using some CPU intensive program won't help no matter how slim your WM is.

After you try out E, try the other ones out (except Matisse). You can have more than one installed at the same time.

One more tidbit. E is not just a WM but also a DE. When you run normal E17, you get a whole desktop. This means you cannot normally use E with GNOME or KDE. A WM by itself will just replace the other WM (Metacity for GNOME and Kwin for KDE) which means you can use a WM like Beryl along side GNOME or KDE.

---

