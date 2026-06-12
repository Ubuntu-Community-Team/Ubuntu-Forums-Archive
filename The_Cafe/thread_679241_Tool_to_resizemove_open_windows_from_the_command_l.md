---
title: "Tool to resize/move open windows from the command line?"
date: 2008-01-26
forum: The Cafe
---

### Post by ZylGadis on 2008-01-26
Hi folks,

I recently got a 24" monitor, and together with my two 17" ones I have a huge working space in Xinerama. The resolution is 4480x1200. I want to write a bash script that automatically starts several programs and resizes/moves their windows the way I tell it to, so that with one command I can have a ready working space with NetBeans, a few browsers with documentation, Emacs, a few terminals, etc. or another one with several Emacs windows, a few browsers with dictionaries, a few standalone dictionaries, OpenOffice Writer, etc. I am sick of rearranging things by hand.

What I am really looking for is some kind of X tool that takes a window (perhaps the most recently created one), resizes it to a size I tell it to, and moves it to a location I tell it to. There seem to be none such.

I've tried all kinds of tiling tools, which do not work for my (admittedly esoteric) setup. I was hopeful of devilspie, but it turned out it cannot distinguish between separate windows of the same program (unless the program is gnome-terminal), so it won't fit my needs. I don't want to dig into the specifics of X, modify the code, recompile it, etc - it is a huge hassle and will waste more time than I can afford.

Suggestions, please?

---

### Post by alien_acorn on 2008-03-07
Try [wmctrl.]("http://www.sweb.cz/tripie/utils/wmctrl/")

---

