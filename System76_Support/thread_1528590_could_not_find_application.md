---
title: "could not find application"
date: 2010-07-10
forum: System76 Support
---

### Post by BuggyFunBunny on 2010-07-10
(may not be specific to S76, but who knows???)

since moving to 10.04 (leaving 8.10 /home as is), adding vim, for example, to the menus fails when picking from the menu, with

could not find application
/usr/bin/vim

which, of course is there, and runs just fine from a terminal.  Oracle, for example, installs itself, including building menus, and they work fine.  

I can't find any information on why menus would be broken for manually created entries.

---

### Post by volkerbradley on 2010-07-11
You're right.  In the Menu Editor, I could find no option to open a command in the terminal.
I tried making an executable shell script that opens the gnome-terminal and then opens vi but I could not do that.
So to solve this problem with vim, I did sudo apt-get install vim-gnome and then changed the command to /usr/bin/gvim

---

### Post by marshmallow1304 on 2010-07-12
You can use

gnome-terminal -x /usr/bin/vim

for the menu item.

---

