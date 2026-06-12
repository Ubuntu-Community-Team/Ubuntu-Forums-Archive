---
title: "do keyboard shortcuts (hotkeys) work in other display environments?"
date: 2019-12-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-09
i run Xubuntu 18.04 LTS which has XFCE version 4.12.  i am using it  keyboard shortcut and am wondering if other display environments, like  Gnome, KDE, LXDE, and so on, support doing this.  i can have them do anu  command i want to do.  i have several set to switch to specific users  and others switch workspaces.  this even works when firefox opens a  site, such as a youtube video, in full screen mode.  they work in full scree mode.

---

### Post by TheFu on 2019-12-09
Yes. They all do.

This has been part of the X11 Window Manager since the early 1990s, perhaps longer.
LXDE uses the openbox WM. There is a config file that controls openbox, including ways to make keyboard shortcuts work.

---

### Post by Skaperen on 2019-12-09
so something outside of xfce carries out the actions but a menu app in each DE sets it?  it sure looked like it was an xfce feature since an xfce menu was pulled up to set it.  i have then found the file the shortcuts are stored in (an XML file).  this lets me do identical settings in all users by copying this file around.  the path to the file is [COLOR=#0000cd][FONT=courier new]**~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xm**[/FONT][/COLOR]l which further made me believe it was an xfce feature.  i'm guessing other DEs store it elsewhere.  but how does the _X11 Window Manager_ get the settings?  i'm guessing that it does not read that file directly.  a library thing?

to change shortcuts i now just edit that .xml file (i have to trick emacs to believe it is not .xml) and re-distribute it.  i'm a long time no GUI just CLI user.  now that hardware is fast enough that a graphical terminal is fast enough, i've moved to GUI so i can access graphical stuff like firefox right along side my CLI terminals.  learning how to do multiple users logged in concurrently, how to switch between them rapidly (shortcuts, more rapid than a menu), and the same for workspaces, this all now beats the old text console.  shortcuts are great for me since i am still very keyboard oriented.

---

