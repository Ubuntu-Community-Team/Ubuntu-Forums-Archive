---
title: "after x server starts keyboard stops working!!"
date: 2009-08-31
forum: Server Platforms
---

### Post by gobbledigook on 2009-08-31
hi

i've been following **_[this ]("http://www.xbmc.org/forum/showthread.php?t=32891")_**how-to to install xbmc on my normally headless machine, but have been having some trouble with the x server.

if i run ```
sudo xinit
``` i get a session start with a blank console but any attempt by me to type into the console using the keyboard simply doesn't do anything!! 

I can't even ctrl+c out of it, i have to either do a hard reset or log in via ssh and kill the x process. 

i installed xbmc using atp-get after adding to my sources.list file the correct repo's and when i try and run it i get:

```

server@server:~$ xbmc
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: unable to open display
FEH.py: cannot connect to X server

```

anybody got ideas?

Dan,

---

