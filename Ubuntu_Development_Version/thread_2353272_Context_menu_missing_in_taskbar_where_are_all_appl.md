---
title: "Context menu missing in taskbar where are all applications window"
date: 2017-02-20
forum: Ubuntu Development Version
---

### Post by alain.roger on 2017-02-20
Hi,


Since last update, all windows/apps opened do not show any popup window when i'm right clicking on the task bar -reduced- window.
Before when i wanted to close the app, i went to task bar, right clicked on the reduced windows of the app, and left click on "close" to terminate the app... now it does not show anymore the popup window.


AFAIK this is called the "operations menu" and everything is set correctly by default in my settings.

[IMG]http://i220.photobucket.com/albums/dd277/alainroger/th_kde-operation-menu-not-working_zpsgbklnbcw.mp4[/IMG]

[IMG]http://i220.photobucket.com/albums/dd277/alainroger/Linux/2017-02-07_Selection_002_zpsqtkhjpnd.jpg[/IMG]

in taskbar where all apps window should be no operation menu appears :(


What's happened ?


My mother has the same issue with Kubuntu 16.04 as me.

we should get both:

[IMG]http://i64.tinypic.com/jaz69f.png[/IMG]

---

### Post by alain.roger on 2017-02-20
Ok after last update of the following packages:
[FONT=monospace][COLOR=#000000]gnome-shell gnome-shell-common gnome-shell-extensions libmutter-0-0 mutter mutter-common[/COLOR]

it works as before :D[/FONT]

---

### Post by jbicha on 2017-02-20
This is a confusing thread because your first post was about KDE and your second post mentions packages that are only used by GNOME Shell (well Budgie also currently uses mutter too).

---

