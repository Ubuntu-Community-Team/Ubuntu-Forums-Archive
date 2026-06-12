---
title: "change to root in dolphin, or konqueror?"
date: 2007-04-21
forum: The Cafe
---

### Post by fuscia on 2007-04-21
this can be done in both thunar and nautilus (in fact, in thunar, one caan just write it as a custom action). can this be done in dolphin? what about konqueror? if not, why not?

---

### Post by me1on on 2007-04-21
In Kubuntu, you can right-click a text file, click actions, then click "edit as root." This only works for text files though; if you want to open anything as root, you could probably [create your own service menu]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html") for it. After you create it, it should appear under the "actions" menu when you right-click a file.

---

### Post by fuscia on 2007-04-21
> **me1on said:**
> In Kubuntu, you can right-click a text file, click actions, then click "edit as root." This only works for text files though; if you want to open anything as root, you could probably [create your own service menu]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html") for it. After you create it, it should appear under the "actions" menu when you right-click a file.

DOH! i'm an idiot! i went to look in the dolphin servicemenus directory (thanks to your suggestion) and it was already there. it *does* appear in 'actions'. thanks for the response. this is great!

edit: no, wait! this is FAAAAAAAAAAAAAAAAABULOUS!!1

---

### Post by fuscia on 2007-04-22
here's a ready made little solution for konqueror - [http://wiki.freespire.org/index.php/Add_Root_Actions_Service_Menu](http://wiki.freespire.org/index.php/Add_Root_Actions_Service_Menu)

---

### Post by perspectoff on 2012-05-05
kdesudo dolphin

will start the Dolphin file manager as the root user (requiring the root password). You can make this command into a menu item.

If you haven't set the root password, do so:

 sudo passwd root

When you open a file from Dolphin once it is opened as the root user (such as with the text editor kate) you will be doing so with root privileges. Very handy.

You can also start dolphin as the root user from the command line using

 sudo dolphin

but you can't use this command as a menu item.

---

### Post by sisco311 on 2012-05-05
Necro.

[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

Thread closed.

---

