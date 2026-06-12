---
title: "Can the devs make the applications menu more editable"
date: 2014-10-19
forum: Ubuntu Studio
---

### Post by jeffmezz on 2014-10-19
[https://drive.google.com/file/d/0B0aJ_7pXV1-EM05yYzZpa24xZnc/view?usp=sharing](https://drive.google.com/file/d/0B0aJ_7pXV1-EM05yYzZpa24xZnc/view?usp=sharing)
Ok I'm experimenting with making UbuntuStudio64 a bit more touch friendly with a bit of a face lift that gives some Androidesqu functions and buttons here is a pic of what I've been doing I'd just like to be able to make the icons in application menu bigger and I'd like the bar to be more like a drawer horizontal possibly sizable...is it possible to do this with an application? As you can see from this pic I've added back button, Touch Keyboard button, System settings button, App menu button App, Home button, search button,and a Forward button. This is all ubuntu really needs to be touch friendly light and simple/familiar. I used an app called xdotool to map keyboard shortcuts to launchers to easily run window commands from terminal.
[IMG]https://drive.google.com/file/d/0B0aJ_7pXV1-EM05yYzZpa24xZnc/view?usp=sharing[/IMG]

---

### Post by QIII on 2014-10-19
Hello!

This is a user forum. Although a developer my wander in here from time to time completely by accident, it is very unlikely that any of them would ever see a question posted here.

I suggest going the the Ubuntu Studio website and seeing if they have a developer mailing list.

Cheers!

---

### Post by jeffmezz on 2014-10-19
Do you know if theres a way to change the applications menu using a program?

---

### Post by ajgreeny on 2014-10-19
Which desktop environment does Ubuntu-studio use and does it use the main menu or whisker menu?

If as, I believe, it is xfce you should be able to edit the contents of the menu with alacarte, which is what is used in Xubuntu for the menu.

You can change the icon size in the whisker menu with a right click and Properties, but I'm not sure about the main menu.
 Have you tried right clicking on the xfce-settings-manager and playing with the settings there for appearance?

---

### Post by Toz on 2014-10-19
> **jeffmezz said:**
> I'd just like to be able to make the icons in application menu bigger
Depends on the version of Xfce and which menuing application you are using. If you are using the Whisker menu, right-click on the menu, choose Properties and set the menu icon sizes. If you are using the default Xfce applications menu, then it depends on which version of Xfce you are using. In 4.10, the following command affects menu icon sizes:
```
xfconf-query -c xsettings -p /Gtk/IconSizes -s "panel-applications-menu=32,32"
```
...change the "32,32" to suit.

For Xfce 4.11, it looks like its changed (or its a bug):
```
xfconf-query -c xsettings -p /Gtk/IconSizes -s "gtk-menu=32,32"
```
...and it affects all menu icon sizes.

> and I'd like the bar to be more like a drawer horizontal possibly sizable
Not sure what you mean.

---

### Post by jeffmezz on 2014-10-20
You know how you can make custom pannels and resize them with row size, number of rows, and row length...Im wondering if theres something I can use to Adjust the applications menu similarly right now its a vertical xfce bar with tiny icons and application names. I would like to make it more like an android style app drawer. By the way thanks for the in depth comment I found it very usefull do you know if there is a command to find out what version of xfce Im running I believe its at least xfce4?

---

### Post by jeffmezz on 2014-10-20
I right click the menu click properties and there is only basic functions in there such as button name and icon and use custom menu file. Is there a way to import a menu file from something other than xfce?
> **ajgreeny said:**
> Which desktop environment does Ubuntu-studio use and does it use the main menu or whisker menu?

If as, I believe, it is xfce you should be able to edit the contents of the menu with alacarte, which is what is used in Xubuntu for the menu.

You can change the icon size in the whisker menu with a right click and Properties, but I'm not sure about the main menu.
 Have you tried right clicking on the xfce-settings-manager and playing with the settings there for appearance?

---

### Post by Toz on 2014-10-20
> **jeffmezz said:**
> do you know if there is a command to find out what version of xfce Im running I believe its at least xfce4?
Open a terminal window and run:
```
xfce4-about
```
...or there should be an "About Xfce" item on the main menu.

---

