---
title: "I want old compiz borders back"
date: 2007-02-16
forum: The Cafe
---

### Post by 4KvRMU7Nnv on 2007-02-16
At first, when i heard that there was metacity support for compiz borders i was excited.  I thought i could now explore new horizons of composited gloriousness.  However i have found that the hack to get there rendered the maximizing uglier and slower (bad resizing buttons, slow, etc) I want the old classic compiz buttons and border back becuase they were really fast and worked perfectly.  Plus i think they looked awesome as well.  Is there any way to get them back???

---

### Post by jranweil on 2007-02-17
*Oddly, I just answered this same question (I think) earlier today, in the Fedora forums.  I will re-post my response here for you.  I tested it in Ubuntu 6.10 (with compiz from the gandalfn repo) and it works there too.*

I also wanted to use the 'default' compiz borders. Here are two ways to do it.
[INDENT](1)  Open either the terminal or the 'run application' dialog (Alt + F2)
(2)  Run this command
[INDENT]**gconftool-2 -s '/apps/gwd/use_metacity_theme' --type bool false**[/INDENT][/INDENT]
If you want to do it graphically, do the following:
[INDENT](1)  Run gconf-editor ("Configuration Editor" under System Tools in the Main Menu)
(2)  Find the keys under '/apps/gwd' via the tree list on the left
(3)  Uncheck the box next to the key name 'use_metacity_theme'.[/INDENT]
The two methods are equivalent, as **gconf-editor** is just a graphical front-end to **gconftool-2**. The borders should change instantly with either method.

If you want to use your metacity theme AND compiz again, run
[INDENT]**gconftool-2 -s '/apps/gwd/use_metacity_theme' --type bool true**[/INDENT]
..or go back and check the use_metacity_theme key in Configuration Editor.

---

### Post by 4KvRMU7Nnv on 2007-02-17
YES!!!! THANK YOU!!! now it won't look so ugly!  i love the default compiz theme! thanks so much

---

