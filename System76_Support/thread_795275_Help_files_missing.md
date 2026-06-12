---
title: "Help files missing"
date: 2008-05-15
forum: System76 Support
---

### Post by glacialfury on 2008-05-15
Not sure if this is Ubuntu's problem or System76, I assume the former.  Some help files do not show up.

Example:  In Terminal

Go to the Help menu, click on Contents.  It brings up the initial Contents page.  Click on Introduction, or Getting Started - the help application shuts down.

---

### Post by thomasaaron on 2008-05-15
It works fine on mine. It is likely a configuration or misplaced files on your system.

Try...

sudo apt-get --reinstall install gnome-terminal gnome-terminal-data

---

