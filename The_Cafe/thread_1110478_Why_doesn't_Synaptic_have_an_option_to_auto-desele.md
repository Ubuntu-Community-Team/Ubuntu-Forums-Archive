---
title: "Why doesn't Synaptic have an option to auto-deselect packages that are dependencies?"
date: 2009-03-29
forum: The Cafe
---

### Post by bobbob1016 on 2009-03-29
I recently installed MythTV on my eeepc to connect to my backend on another machine.  I then realized that it'd be a pain getting it working quickly remotely, so I went into synaptic to completely remove all myth things from my eeepc.

However, one package wanted to remove plugins-bad.  Now I have to hunt down which package I selected is a dependency.  Wouldn't it be logical to include an option to save the selected packages, as in "select the packages you want to keep, and the dependencies you selected to remove will be automatically unchecked"?  Or am I missing an obvious button?

---

### Post by MaxIBoy on 2009-03-29
Hard to understand your question, so here are a bunch of possible answers.

To see a list of all installed packages, go to a terminal and run "dpkg -l." To save the list to a text file somewhere, pipe the command through to a text file like this: "whatever_command > text_file.txt". To save a list of all the dependencies of a package, run "apt-rdepends name_of_package". If you can't remember the exact name of the package, use "apt-cache search insert_keywords_within_quotes_here" to find the name.


If you want to automatically remove unneeded old packages that were installed as dependencies of something you don't want anymore, there are a number of methods for this.

[LIST]
[*]My favorite method is to pull up a terminal and run the command "sudo apt-get autoremove," which uninstalls all programs that are no longer needed. Just type in your password when prompted for it; if nothing shows up on the screen it's normal.
[*]You can also go to Synaptic. In the lower right area there will be a button that says "status." Click on that. The bar above it will change to a different list. Click on the entry that says "installed (auto-removable)," and you'll get a list of all the packages that aren't being used.
[/LIST]

---

### Post by bobbob1016 on 2009-03-30
I realized it was confusing as I was typing.

Basically, I was saying when I try to do completely remove on a large group of programs, and it says "These programs will also be removed" it's a pain to find the program I need to keep to keep one of the "These programs will also be removed".

For example, If I like amarok in my gnome, and I try out kde, and then want to purge kde 100% but I want to keep amarok, I'd either have to know what I need to leave installed for amarok, or just reinstall it.  The feature I was asking about would allow me to simply select to remove ALL kde apps in this example, and say "Amarok will also be removed" and then have a "Keep this program installed option" to automatically not deselect amarok and it's dependencies.

---

### Post by etnlIcarus on 2009-03-30
The best way to do what you're suggesting is to remember which meta-package you originally used to install, say KDE. When you remove the KDE meta-package, all the KDE dependencies which aren't currently being used by any other apps and can be safely removed appear in Status>Automatically Removable in the side-pane of Synaptic.

---

### Post by bobbob1016 on 2009-03-30
I just thought it'd be a good feature if I forgot the meta-package, or if I'm removing multiple things at once, as in going through and removing old programs to cleanup my PC.

---

