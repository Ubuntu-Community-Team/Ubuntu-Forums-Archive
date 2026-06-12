---
title: "HOWTO for Xubuntu: use dmenu to launch applications in XFCE"
date: 2011-05-02
forum: Tutorials
---

### Post by keithpeter on 2011-05-02
Hello All

Xubuntu 11.04 uses the XFCE desktop environment which provides a shortcut for maximising a window so that the window decoration (title bar &c) does not show and so the window covers the panels. Alt-F11 is the shortcut assigned to this.

I like to bring other applications up while using (say) OpenOffice maximised in this way. There is a shortcut that will bring up the main menu (ESC-Ctrl), but then you have to navigate the menu.

This miniHowTo explains how to use the dmenu program from the dwm window manager (in repositories) to launch applications by pressing a short cut (I've set mine to Super/Windows-Space), typing the name of the application, and pressing enter. The new application window has focus.

This howto has been tested on a stock install of Xubuntu 11.04 using compositor. I have no idea if it will work with compiz or other window managers with effects enabled. Feedback on that or any other aspect is welcome.

**Step 1: install dmenu**

From terminal, run

```
sudo apt-get install dmenu
```

and type your admin password

Apt will tell you that dmenu is part of the 'suckless tools package' and mention the window manager dwm, and then proceed to install this very small command line program.

**Step 2: Populate a cache of all the applications available in the /usr folder**

From terminal run the command

```
dmenu_path
```

and you should see a list of applications printed to the terminal screen. This list is also saved as .dmenu_cache in your home directory. You *may* need to run this command again when you install software, when I installed Seamonkey using the Ubuntu Software Centre the cache was automatically updated.

**Step 3: Test from terminal**

From terminal run the command

```
dmenu_run
```

You should see a list of applications appear in a 'terminal' style font at the very top of your screen on top of the upper panel.

Type the name of a program (e.g. 'mousepad'). As each letter is typed you should see the applications that match the currently typed letters appear in the line at the top of the screen.

When you have typed enough letters so that only the application you want appears, press the enter key. The application should load.

You can press ESC to abort a search and quit dmenu_run. The terminal is matched as x-t, short for x-terminal-emulator. I'm fiddling with aliases and the application cache to try to define more user meaningful names.

**Step 4: add a shortcut to XFCE**

I chose to bind the key combination Super-Space to dmenu-run. XFCE 4.8 allows you to define key shortcuts to any program using the settings manager. Just 

[LIST]
[*]Select **Menu | Settings | Settings Manager** from the main menu
[*]Click the **Keyboard** icon in the Settings Manager
[*]Click the **Application Shortcuts** tab
[*]Click **Add**
[*]Write dmenu_run in the command box that appears
[*]When prompted for the short cut keys, press **Super** and **Space** (or the combination you prefer)
[*]If the combination is in use, you will see an error message and be invited to type another
[*]Click **OK** and close the Settings Manager and Keyboard windows
[*]Test your new shortcut
[/LIST]

**References**

dmenu man page at [http://man.suckless.org/tools/1/dmenu](http://man.suckless.org/tools/1/dmenu)
keyboard shortcut at [http://ubuntuforums.org/showthread.php?t=944456](http://ubuntuforums.org/showthread.php?t=944456)

---

### Post by casbahdk on 2011-09-10
Thanks for the HowTo, it was very useful. I am using the following command in an attempt to get dmenu to blend in more with the default theme. Unfortunately, I can't get the text set to #FFFFFF (white) when not highlighted.```
dmenu_run -i -nb '#B5B1B1' -nf '#FFFFFF'
```
----
Edit
Well, the following is a lot easier on the eyes, but I can't specify font or size for some reason.```
dmenu_run -i -nb '#000000' -nf '#FFFFFF'
```

---

