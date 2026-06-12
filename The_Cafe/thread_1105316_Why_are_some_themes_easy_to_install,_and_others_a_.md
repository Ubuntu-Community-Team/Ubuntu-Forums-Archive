---
title: "Why are some themes easy to install, and others a grand mystery?"
date: 2009-03-24
forum: The Cafe
---

### Post by diablo75 on 2009-03-24
A blog posting someone put up has a nice collection of 50 available themes for Ubuntu.  Here's the blog:  [http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/](http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/)

The problem is that, while some of these themes can be installed by simply dragging and dropping the archive files into Ubuntu's theme manager, others don't work that way.  In some cases, I can't tell if it's even an archive (what the heck is an xpi file??).

Are there any comprehensive guides out there for installing themes?  I wish I didn't have to look for something like this because it seems kind of weird to have some themes that "just work" being placed along side others that take a psychic to get them to install.

And on the side, is there any effort being made out there to have some sort of standard theme building and distribution guidelines made so that when you go to download a theme that says it's made for GTK, you can be rest assured it will work when you drag it into your theme manager?  If it were up to me, I'd start it off by saying something like:

Rule 1:  Include a readme.txt file with clear installation instructions.

That'd be a nice start.  Sorry for the rant...

---

### Post by smbm on 2009-03-24
I believe an xpi file is a Firefox theme.

---

### Post by Icehuck on 2009-03-24
> I believe an xpi file is a Firefox theme. 

Yeah, XPI are zip archives that firefox uses.

---

### Post by 23meg on 2009-03-24
> **diablo75]The problem is that, while some of these themes can be installed by simply dragging and dropping the archive files into Ubuntu's theme manager, others don't work that way.[/QUOTE]

That would happen either because the theme archive is packaged in a non-standard way by the author, or because you don't have the necessary theme engine installed.

When you drag and drop an archive file on gnome-appearance-properties, it's checked for validity and extracted to your ~/.themes folder. Some authors distribute more than one theme in a single archive, and historically that made it impossible for gnome-appearance-properties to install them successfully, and you had to extract those themes one by one to your ~./themes folder. Starting with GNOME 2.24, it can deal with multiple themes in one file (possible enhancement: it should deal with multiple archive files contained in an archive file as well).

[QUOTE=diablo75]And on the side, is there any effort being made out there to have some sort of standard theme building and distribution guidelines made so that when you go to download a theme that says it's made for GTK, you can be rest assured it will work when you drag it into your theme manager? [/QUOTE]

Look into the folders under your ~/.themes folder to see the file layout said:**
> If it were up to me, I'd start it off by saying something like:

Rule 1: Include a readme.txt file with clear installation instructions.

That would be somewhat inconsistent with your above description; if the theme needs to "just work", why do I need a readme file with a list of instructions that I have to follow to make it work?

---

