---
title: "Subtle Marco Compositor Bug"
date: 2022-03-25
forum: Ubuntu Development Version
---

### Post by sgage on 2022-03-25
Here's a subtle and obscure buglet in UM 22.04 for you: When using the Marco window manager with its built-in compositor enabled, a strange graphical glitch appears. So far I have only observed this with Firefox (deb, tar.gz, or snap, makes no difference) and Thunderbird, so there seems to be a Mozilla component to it. So here it is:

With the FF or TB window maximized, the bottom boundary of the window title bar is glitched - sort of broken up in a couple of places, one to the left and one right of center. I told you it was subtle :KS  When the program is windowed, that glitch goes away. This happens in no other distro that I use (I experiment with MATE on various distros), and it does not happen with Marco's compositing turned off. (I would just leave it off except then the tool tips for the Plank Dock are solid black).

Fully updated Ubuntu MATE 22.04 as of 15:45 EDT (US East coast)
Firefox is version 98.0.2
Thunderbird is version 91.7.0
Marco is 1.26.0-2

Graphics are Intel HD Graphics 630

---

### Post by sgage on 2022-04-04
[post deleted - I spoke to soon]

---

