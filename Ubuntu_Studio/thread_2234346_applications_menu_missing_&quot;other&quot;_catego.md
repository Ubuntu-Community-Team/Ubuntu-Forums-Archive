---
title: "applications menu missing &quot;other&quot; category"
date: 2014-07-14
forum: Ubuntu Studio
---

### Post by a-you on 2014-07-14
I just installed ubuntu studio trusty tahr from scratch (didn't upgrade) and for reasons beyond understanding the "Applications Menu," which is otherwise working fine, is missing the "Other" category. There are launchers listed under "Other" so apparently that's not why. In fact firefox is listed there even (I didn't put firefox there, but it's added to that category) and firefox is definitely installed and working. I have no idea where to look. I've searched and searched but didn't come across anything on the interwebs that would seem to explain this at all (sorry if I missed something obvious; I don't think I did).

If anybody knows how to fix this---to have the "Other" sub-menu work---I'd appreciate it a lot!! Thanks in advance!

---

### Post by Toz on 2014-07-14
I'm using Xubuntu so the specifics may be a little different, but both flavours use Xfce as the desktop environment and they implement the menu spec in the same way.

The [Freedesktop menu spec]("http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html") explains how it should work. 

In a nutshell, the application's .desktop file (located in either /usr/share/applications or $HOME/.local/share/applications) lists the "Categories" that apply to the applications that align with the menu categories. The application will show up in the first category in the apllication's "Categories" list that matches with a category supported by the menuing application that you are using (note: Other is also a catch-all category for those that don't match any category). The "Other" sub-menu will only show up if there is an item to display.

The sure-fire way to get an application to show up in the "Other" category is to change the application's "Categories" line to contain only "Other;" (or leave it blank).

For example, here are the relevant entries from the xchat.desktop file:
```
[Desktop Entry]
Encoding=UTF-8
Name=XChat IRC
Comment=Chat with other people using Internet Relay Chat
Exec=sh -c "xchat --existing --url %U || exec xchat"
Icon=xchat
Terminal=false
Type=Application
Categories=Network;
StartupNotify=true
MimeType=x-scheme-handler/irc;x-scheme-handler/ircs;
```
The category "Network" aligns with the Internet submenu (see /usr/share/desktop-directories/xfce-network.directory and the relevant xfce-applications.menu file if you want to trace it).

If you change:
> Categories=Network;
...to:
```
Categories=Other;
```
...it will display and show up in the Other sub menu (you may need to "xfce4-panel -r" to have it display).

As for firefox showing up in the menu editor's "Other" category (I'm assuming that you are using alacarte as the menu editor) but not in the Other Menu, have a look at the "Categories" entries in /usr/share/applications/firefox.desktop and you'll find that it will match a category in that list and thus show up in the relevant submenu. In addition, one of the entries in that list will not match up with a known category and will then be interpreted as "Other".

---

### Post by a-you on 2014-07-14
Thanks a lot. The most frustrating part of things not showing up was the prospect of having to edit the menu with the gui, which unfortunately is not one of the more elegant features of gnu/linux at the moment (extremely alow process to add an item, move it up/down, etc.) So thanks for pointing out where the .desktop files are(!!!) because I expect one can edit those with a text editor and it should work just as well.

---

### Post by Toz on 2014-07-14
> **a-you said:**
> Thanks a lot. The most frustrating part of things not showing up was the prospect of having to edit the menu with the gui, which unfortunately is not one of the more elegant features of gnu/linux at the moment (extremely alow process to add an item, move it up/down, etc.) So thanks for pointing out where the .desktop files are(!!!) because I expect one can edit those with a text editor and it should work just as well.

Xubuntu 14.04 introduced xfce4-whiskermenu-plugin as the new Xfce menuing application. One of its benefits is that allows for easier editing of the main application menu (including categories). You might want to consider giving it a look. You can find it in the official repositories.

---

### Post by a-you on 2014-07-15
Ah, though you didn't say it directly, I realized that I had spoken wrongly: the slow editing via alacarte is just alacarte! Not gnu/linux!! I still have some mental habits from years of using one of those other OSes (Apple's). Gradually I unlearn all that propaganda about you've got one way to do things, one application that they package for you, etc. Funny.

Thanks for the tip about xfce4-whiskermenu-plugin. Just installed it and it looks excellent. Also the menulibre editor looks like a very excellent app!!! (so far I've just glanced at both but they seem very nice.)

Also btw in the properties dialog for whiskermenu one can change the "switch user" setting to use
```
 dm-tool switch-to-greeter
```
For some of us "switch user" was broken. This fixes that.

Whew.

---

### Post by a-you on 2014-07-16
I spoke too soon... menulibre worked one time, then crashed the next time I tried to use it, now it refuses to even launch. If I try to launch it by typing menulibre into the terminal window then these error messages return:

```
 ** (menulibre:4630): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-Hnd6kiixZm: Connection refused
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated. please move it to /home/<my_user_name>/.config/fontconfig/fonts.conf manually
**
ERROR:/build/buildd/gnome-menus-3.10.1/./libmenu/gmenu-tree.c:4022:preprocess_layout_info: assertion failed: (!directory->preprocessed)
Aborted (core dumped)
```

Restarting does no good, neither does purging and then reinstalling menulibre.

Not only that but menulibre rearranged the menus in a way that they're clearly screwed up (to try to describe how would take too long and isn't too relevant I don't think anyway). It's clear that it was the test I made of trying menulibre the first time that rearranged the menus too.

But ALSO now alacarte was just crashing upon launch!!! After several attempts to get at least alacarte running it finally launched, but clicking the button it offers to restore the default menus did no good; they're still in the screwed up arrangement that menulibre left them in.

Menu editing has so far proven to be kind of frustrating. Maybe the menu system really needs some basic redesign work, I don't know...

If anybody has any ideas please tell me (thanks).

[update:] I tried removing ~/.config/menus/xfce-applications.menu and that has allowed both alacarte and menulibre to launch, also alacarte's button to restore the stock menus seems to have worked after removing that (whew). Now I'll try editing menus with menulibre again, but I think I won't mark this "solved" until it's clear that it really worked.

No, it's quite hosed. It seems that making any sort of change using menulibre causes a new ~/.config/menus/xfce-applications.menu to be created and at the same time causes menulibre not to run next time one tries to launch it. I guess it's back to the old slow process of using alacarte...

---

### Post by Toz on 2014-07-16
That's odd. I've used both menu editors and haven't experienced a crash like this one.

> It seems that making any sort of change using menulibre causes a new ~/.config/menus/xfce-applications.menu to be created 
This is normal. When you edit the menu, it will create ~/.config/menus/xfce-applications.menu as your new edited menu. If you're willing, can you post this menu when the crashing starts so I can have a look at it?

Otherwise, try making one menu change at a time to try to determine which change it is that is causing the crash.

---

### Post by a-you on 2014-07-17
Thanks for yout comments again. Actually that's a good point: in each case the change that I tried to make was to open a menu item for editing in menulibre and then to delete 1 or 2 categories, then save the changes. I wonder, have you tried something like that??? I happen to prefer that an app is listed in only one category and so this has tended to be the first thing I spontaneously did each time I tried using menulibre.

[added a bit more:] To be honest I'm a bit reluctant to test menulibre until I know how to fully back up the menu that I have, because last night I spent hours slowly one at a time checking each item that was listed in one of the 3 weird "Unused" menus that had been created to see that it was also listed in another menu, and if it wasn't to craete an entry for it. Anyway the point is only that I *think* (though it's hard to say for certain in retrospect) that the process of recovering from a crash of menulibre required me to open alacarte and click the button to restore the default menus, which would put me back at the start!

So may I ask: do you know what all the files are that pertain to menus?? I mean, there are the .desktop files in /usr/share/applications and in ~/.local/share/applications, then there's ~/.config/menus/xfce-applications.menu. Are there any others I should be aware of?? (Thanks again!)

---

### Post by Toz on 2014-07-17
> **a-you said:**
> So may I ask: do you know what all the files are that pertain to menus?? I mean, there are the .desktop files in /usr/share/applications and in ~/.local/share/applications, then there's ~/.config/menus/xfce-applications.menu. Are there any others I should be aware of?? (Thanks again!)

.desktop files are also read from /usr/local/share/applications (if it exists). 

.directory files are read from /usr/share/desktop-directories, /usr/local/share/desktop-directories and ~/.local/share/desktop-directories.

.menu files are read from $XDG_CONFIG_DIRS/menus (the first valid entry taking precedence), as well as ~/.config/menus.

.desktop files in ~/.config/menus/applications-merged are also merged in.

A more complete description can be found in [http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html]("http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html"):
>  Here are the files defined by this specification:

**$XDG_CONFIG_DIRS/menus/${XDG_MENU_PREFIX}applications.menu**

    This file contains the XML definition of the main application menu layout. The first file found in the search path should be used; other files are ignored. This implies that if the user has their own ${XDG_MENU_PREFIX}applications.menu, it replaces the system wide one. (Though the user's menu may explicitly merge the system wide one.)

    Systems that offer multiple desktop environments and that want to use distinct menu layouts in the different environments can use differently prefixed .menu files. In this case the $XDG_MENU_PREFIX environment variable must be set by the system to reflect the .menu file that is being used.

    For example if a system contains both the GNOME and the KDE desktop environments it can decide to use gnome-applications.menu as the menu layout in GNOME sessions and kde-applications.menu as the menu layout in KDE sessions. To correctly reflect this, it should set the $XDG_MENU_PREFIX environment variable to "gnome-" respectively "kde-".

    Implementations may chose to use .menu files with other names for tasks or menus other than the main application menu. Such usage is not covered by this specification. 

**$XDG_CONFIG_DIRS/menus/applications-merged/**

    The default merge directories included in the <DefaultMergeDirs> element. By convention, third parties may add new <Menu> files in this location to create their own sub-menus.

    Note that a system that uses either gnome-applications.menu or kde-applications.menu depending on the desktop environment in use must still use applications-merged as the default merge directory in both cases.

    Implementations may chose to use .menu files with names other than application.menu for tasks or menus other than the main application menu. In that case the first part of the name of the default merge directory is derived from the name of the .menu file.

    For example in a system that uses a preferences.menu file to describe an additional menu, the default merge directories included in the <DefaultMergeDirs> element in the preferences.menu file would become $XDG_CONFIG_DIRS/menus/preferences-merged/ 

**$XDG_DATA_DIRS/applications/**

    This directory contains a .desktop file for each possible menu item. Each directory in the $XDG_DATA_DIRS search path should be used (i.e. desktop entries are collected from all of them, not just the first one that exists). When two desktop entries have the same name, the one appearing earlier in the path is used.

    The <DefaultAppDirs> element in a menu file indicates that this default list of desktop entry locations should be scanned at that point. If a menu file does not contain <DefaultAppDirs>, then these locations are not scanned. 

**$XDG_DATA_DIRS/desktop-directories/**

    This directory contains directory entries which may be associated with folders in the menu layout. Each directory in the search path should be used. Only files ending in .directory are used; other files are ignored.

    The <DefaultDirectoryDirs> element in a menu file indicates that this default list of directory entry locations should be scanned at that point. If a menu file does not contain <DefaultDirectoryDirs>, then these locations are not scanned. 

To see where the environment variables point on your system, run this command:
```
env | grep XDG
```

---

### Post by a-you on 2014-07-17
Thanks a lot.

---

### Post by Toz on 2014-07-17
It doesn't look like you're alone in your issues: [https://bugs.launchpad.net/menulibre]("https://bugs.launchpad.net/menulibre")

EDIT: Looks like there is a PPA for daily builds that will have a more recent, hopefully less buggy version. Keep in mind it is a dev version, so it may have other issues of its own: [https://launchpad.net/~menulibre-dev/+archive/ubuntu/daily]("https://launchpad.net/~menulibre-dev/+archive/ubuntu/daily")

---

### Post by a-you on 2014-07-17
I had added the PPA already and tried it but it was the same. But thanks a lot for the tip.

I'll keep checking for updates to menulibre. Thanks again for all of your comments. It's really appreciated.

---

