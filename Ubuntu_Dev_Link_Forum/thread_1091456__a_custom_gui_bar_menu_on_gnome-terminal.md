---
title: "_a custom gui bar menu on gnome-terminal?"
date: 2009-03-09
forum: Ubuntu Dev Link Forum
---

### Post by Steveuntu on 2009-03-09
I think that could be useful, to add some customized menus to gnome-terminal gui, (ie, to add a menu-submenu with usual and complex shell tasks ...)

Which file (almost terminal.xml i think) must i modify in order to some customized gtk menus?

Thanks a lot for your help,

Steve,

---

### Post by Brucevdk on 2009-04-18
You'll indeed have to edit terminal.xml (which is the definition file for the menubar) but to actually do something you'll have to grab the source for gnome-terminal and make some modifications.

Here's how I usually go about doing such things:

```

$ svn co http://svn.gnome.org/svn/gnome-terminal/trunk gnome-terminal
$ cd gnome-terminal/
$ find -name *.c | xargs grep -i -n "Keyboard Shortcuts"
./src/terminal-window.c:1624:      { "EditKeybindings", NULL, N_("_Keyboard Shortcuts…"), NULL,

```

This shows that the relevant code is in terminal-window.c:terminal_window_init and shows that you can attach callbacks to menu items. You'll have to figure out by yourself how to actually insert text into the terminal window.

To actually compile and install gnome-terminal after making the needed modifications you can do:

```

sudo apt-get build-dep gnome-terminal
./autogen.sh --prefix /usr/local
make
sudo make install

```

Good luck.

---

