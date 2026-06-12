---
title: "Can someone confirm a bug in K-3d"
date: 2008-08-13
forum: The Cafe
---

### Post by Nostrafus on 2008-08-13
Didn't know where to place this, wanted to see if someone can confirm a glitch before bringing it to the k3d team's attention

I ran into a glitch when running the tutorials.  When attempting to do a GTSBoolean the program crashes with the following error message.

> john@john-desktop:~$ k3d
 ERROR discarding empty changeset [Replace].  Context: void libk3dngui::selection_input_model::implementation:: on_button_click(libk3dngui::viewport::control&, const GdkEventButton&)
Segmentation fault
john@john-desktop:~$ 


System Log shows this error message

Aug 13 06:53:03 john-desktop kernel: [52124.725445] k3d-bin[20889]: segfault at 00000000 eip b3ebe1ea esp bfe571b0 error 4

Steps

1: Run k3d
2: Run tutorial #5, during creation of the GTSBoolean with the Cube & Sphere program terminates.

This happens in both KDE, and Gnome, I've uninstalled & reinstalled, same thing.

All information I've found on the Segfault is unrelated, just want to see if it's a bug, or just my system.

---

