---
title: "How to..."
date: 2007-02-15
forum: Ubuntu Customization Guide
---

### Post by draco86 on 2007-02-15
I have installed GNOME, XGL and Beryl and I have a this problem:

I don't know how to change the icons, the shape and the color of the windows.

I talk about the part of the windows where there are the files menù, the navigation icos and the navigation bar.

I tryed to change the gnome theme and the beryl theme but that part of the windows doesn't change

---

### Post by louis_nichols on 2007-02-15
Those are changed from System>Preferences>Themes.

Generally, a GUI is formed of some distinctive parts, each separatelly configurable and customizable:

[LIST=1]
[*]the window manager is the application that handles the place of a window on the desktop, their order on the z axis, their size and that draws the window border. Beryl uses Emerald, with the nice transparent borders. The default in gnome is Metacity and there are many others. You can configure emerald with the option you already know. Metacity can be configured pretty easily too, but it doesn't matter anymore, does it? :)
[*]then there is the way applications look. This is generally referred to as the GTK theme for Gnome and the QT theme for KDE. These are 2 different toolkits that are used to create visual software apps. The GTK theme in Ubuntu can be selected independently of everything else if you go to System>Preferences>Themes>Theme details>Applications tab (or something like this - I am not at my machine right now.)
[*]then there are the Icons. These are usually set via themes and can be selected under System>Preferences>Themes>Theme details>Icons. In the default Ubuntu theme, the mouse cursor is included in the icon theme. And some other icon themes also include the mouse cursors, but
[*]the mouse cursors can be selected separatelly. this is done by using synaptic to install a little app called gcursor, which will create an option to change mouse cursors in the Preferences sub-menu. Then you can install extra mouse cursors from synaptic and use them.
[/LIST]

Hope this has shed some light on the matter. :)

EDIT: typos

---

