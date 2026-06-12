---
title: "Minimal X11; Wine; Message-Only window"
date: 2008-07-02
forum: Server Platforms
---

### Post by DA_uf on 2008-07-02
When I run my application with Wine on Ubuntu 8.04 LTS Server Edition - Supported to 2013, I get:
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

This may just be a matter of installing and starting a minimal X11 on this server edition.  How do I install and start it?  I tried [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

First I thought, I don't need/want a window manager, so I only did:
sudo apt-get install xserver-xorg x-window-system-core
I received the same error and tried:
DISPLAY=:0
export $DISPLAY
sudo startx &
sudo startx -- :0 &
and also tried to install the WM
sudo apt-get install openbox
Still the same error.

The Message-Only window works fine in Wine on a Mac running X11, but I already have the GUI setup.

So how do I install (and start) a minimal X11 on Ubuntu Server?

[RESOLVED]
Thanks to plumcreek's post [http://ubuntuforums.org/showpost.php?p=5114667&postcount=8](http://ubuntuforums.org/showpost.php?p=5114667&postcount=8)

The following was sufficient for my needs (I didn't need x11-apps; I have my own custom app):
1)Install xauth
sudo apt-get install xauth
2)Log out and then ssh back in (with the -X flag)
ssh -X username@hostname
3)Run my Message-Only Wine app
wine myMOwineApp.exe

There were still errors about the fixme and a new font error, but I don't need the fonts and my app runs.  It took something like a 288K install.

On a Mac (which I thought may be an additional issue), it ran from X11.app and from Terminal.app.  If launched from Terminal.app, X11 launches automatically (if you have X11 already installed -- satisfying the "(assuming you are connecting from a graphical Linux host)" clause).

---

### Post by eriqjaffe on 2008-07-03
```
sudo apt-get install xorg
```Should be all you need to install.

---

### Post by DA_uf on 2008-07-03
Thanks.  But it turns out that xorg was 102 packages for 66.6MB while xauth was 3 packages for 299KB.  (See edited original post.)

Hopefully everything I need is now present.

---

