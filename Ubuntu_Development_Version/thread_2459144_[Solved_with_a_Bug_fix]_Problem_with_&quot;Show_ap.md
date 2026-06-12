---
title: "[Solved with a Bug fix] Problem with &quot;Show application&quot; and opened windows"
date: 2021-03-11
forum: Ubuntu Development Version
---

### Post by blackdiamond on 2021-03-11
Hi guys! I've got a strange behaviour testing Ubuntu Hirsute Hippo! 
After the last update if I try to click on "Show application" , if i have one or more windows open, they overlap with the icons in "Show application".
I think it's a little bit annoying, because you have to close all the windows in order to correctly view icons in show application.
Anyone with the same problem?
Is it a bug or something else? 
thank you and have a nice day!

In order to be more clear I'll attach a [screenshot]("https://ibb.co/8YpwwTF")!

---

### Post by corradoventu on 2021-03-12
I see the same problem in both Xorg and Wayland sessions. I opened a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1918874](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1918874)
please subscribe to my bug if you have the same problem and a launchpad account.

---

### Post by corradoventu on 2021-03-29
This bug was fixed in the package mutter - 3.38.4-1ubuntu1

---

