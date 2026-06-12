---
title: "Getting Gnome to use a Wine program to open Windows filetypes with a certain suffix"
date: 2009-08-29
forum: Wine
---

### Post by taslinux on 2009-08-29
A Windows program I use runs great under Wine 1.0.1, and I can start the program using a Gnome panel or desktop launcher pointed to Wine.

What I would like to do is associate certain filetypes with that program. If the Windows app was a music player, for example, I could write a little bash script which opens the Windows player in Wine, then tell Nautilus that all filetypes of that kind should be opened using that script. (Works fine, I've tried this.)

The problem is that the filetypes I need to associate are seen by Nautilus as plain text documents. If I associate one of these with the Wine/Windows program, then ALL plain text documents will open that way by default.

How do I get Nautilus to see these particular text files as special, so I can associate them with the Windows program? They all have a certain filename suffix (call it ".xyz"),

---

### Post by taslinux on 2009-09-09
Problem solved with help from Ubuntu forums:

[http://ubuntuforums.org/showthread.php?p=7919796](http://ubuntuforums.org/showthread.php?p=7919796)

---

