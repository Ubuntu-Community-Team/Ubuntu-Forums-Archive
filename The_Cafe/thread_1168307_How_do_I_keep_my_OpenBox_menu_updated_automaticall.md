---
title: "How do I keep my OpenBox menu updated automatically?"
date: 2009-05-23
forum: The Cafe
---

### Post by gymophett on 2009-05-23
I have lots of apps I need to install and I have no idea how to put them in my menu, and I don't want to run terminal every time I want to open an App, I'm a GUI person.
So can someone help me out? Thanks. :)

---

### Post by Xbehave on 2009-05-23
IS update-menus not enough?

---

### Post by gymophett on 2009-05-23
> **Xbehave said:**
> IS update-menus not enough?

Well, if something like that worked, then that would be fine.

```
gavin@gavin-laptop:~$ update-menus
bash: update-menus: command not found

```

---

### Post by RedSquirrel on 2009-05-23
The Debian menu should take care of that (for the most part). Install the menu package:

```
sudo apt-get install menu
```That will generate a menu for Openbox and it will keep it up to date automatically when you install new software.

---

### Post by CJ Master on 2009-05-24
Copy and past from crunchbang FAQ:

> How do I go about getting an auto updated menu in Openbox?

The Debian menu is disabled in the default CrunchBang install. Follow these instructions to enable it:

    *
      Open the file ~/.config/openbox/rc.xml and find the following section near the bottom:

<!-- system menu files on Debian systems 
<file>/var/lib/openbox/debian-menu.xml</file>
<file>debian-menu.xml</file> -->

Change it to look like this:

<!-- system menu files on Debian systems  -->
<file>/var/lib/openbox/debian-menu.xml</file>
<file>debian-menu.xml</file>

Save the file and exit.

    *
      Install the menu package with the following terminal command.

sudo apt-get install menu

    *
      Add the following line to ~/.config/openbox/menu.xml where you would like the menu to appear:

<menu id="Debian" />

    *
      Restart or reconfigure your Openbox session.



---

