---
title: "Best distro for development (terminal, tiling, keyboard)"
date: 2015-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by andrea-cimatoribus on 2015-05-17
Hi all, a request for suggestions (or is it maybe an idea for a new distro?).

A bit of background: I have been a linux user for 10+ years now, and tried many different distros, mostly but not exclusively debian-based. I use my laptop almost exclusively for using the terminal (terminator), editing text files (emacs), reading emails (thunderbird, even if it's getting outdated-ish) and navigating the internet (firefox, midori), reading pdf files (evince, okular), listen to music (guayadeque). I use a little bit of inkscape and gimp once in a while, not much else. At the moment I am running Mint cinnamon and xubuntu on my two machines. They are ok but could be better.

I have long noticed that, for the things I do, the least I touch the mouse the better. For this reason, I have always been interested in using tiling WMs. I actually used i3 for a while and, while I found it great, I had to abandon it since it messes up the shape of the figures I produce with matplotlib (a python plotting library). On top of that, having to stare at the screen for quite some time every day, I was less than happy with the estetics of i3, not only window decorations, but font rendering was kind of tiring. xfce and cinnamon both have some interesting tiling features, but they imply using the mouse to snap the windows on the sides, and this is kind of annoying, it would be much better if they were tiling by default, at least when I am using the terminal (e.g. on some desktops only).

So, do you know of any distro and/or desktop environment that ticks these following points? (or can you suggest me a way to configure some distro to tick them?)

- fast, lightweight distro, with up-to-date browser, email and calendar apps.
- stable: "ubuntu-style" stable not "debian-style" stable
- pleasant aesthetics, in particular font rendering, better if it is clean and elegant overall
- keyboard-based, doesn't matter if it has a steep learning curve
- tiling capabilities, better if this can be turned on/off on demand (e.g. possiblity to switch from tiling to stacking, or tiling on some desktop only, or for some program only)

At the moment I am considering to move to xubuntu 15.04 (the newest xfce has some interesting improvements in particular concerning the panel), or give it a try to elementary or possibly kaos (but I am afraid of having to reconfigure kde completely, it's been a long time since I last used it). However, since I don't have too much time to test and try, I wanted to collect some ideas here first, maybe there's something else that I missed.

Cheers

---

### Post by cmcanulty on 2015-05-17
I switched to xubuntu a couple of years ago after the unity change. I first did gnome classic but that got to be a constant tweak hassle. Xubuntu seems to me the best compromise between a traditional desktop and still able to configure as I wish and speedy. I look for function and ease of accessing work things rather than fancy effects

---

### Post by Toz on 2015-05-17
> **andrea-cimatoribus said:**
> xfce and cinnamon both have some interesting tiling features, but they imply using the mouse to snap the windows on the sides, and this is kind of annoying,
Just to clear up this mis-conception about Xfce, you can set keyboard shortcuts for the tiling functionality. Xubuntu doesn't have any set by default, but the interface is there. If you go to Settings Manager >> Window Manager >> Keyboard tab, you'll find the "Tile window..." actions down in the list. Simply set the keyboard shortcut that you want to use.

Also, the tile effect when you move a window to a screen edge with your mouse can be toggled via:
```
xfconf-query -c xfwm4 -p /general/tile_on_move -T
```
...you can assign that to a shortcut key. However, this only stops the mouse dragging a window to the edge tiling, it won't prevent the "Tile window..." shortcuts from working.

---

### Post by andrea-cimatoribus on 2015-05-18
> **Toz said:**
> Just to clear up this mis-conception about Xfce, you can set keyboard shortcuts for the tiling functionality. Xubuntu doesn't have any set by default, but the interface is there.

Interesting, I am always busy with other stuff, and I never take the time to dig into these kind of things. Thanks.

---

