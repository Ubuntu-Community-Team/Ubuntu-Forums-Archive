---
title: "I love this desktop, is there any way to get a similar result on GNOME?"
date: 2008-03-31
forum: The Cafe
---

### Post by Mazza558 on 2008-03-31
This is the Web-based OS, EyeOS, and features a task panel on the bottom, and a very nice app menu at the top. (see the attachment)

I was wondering if it was possible to recreate that desktop on Ubuntu, with multiple menus at the top. As far as I know, the gnome app menu only has Apps, Places and System, and I'd like to be able to have just Icons for each, and also categories of apps. I thought of AWN, but I don't think it can be moved to the top of the screen, let alone not show open apps and have menus for categories.

Any ideas?

---

### Post by Wobedraggled on 2008-03-31
The metabox theme will give you similar window iborders, and the mist icon set might be a good match.

---

### Post by aaaantoine on 2008-03-31
Find the source code for the **Menu Bar** gnome-panel applet.  You might be able to replace Applications, Places, and System with just icons.  Depending on the type of widget used to create the Applications button, you might be able to just copy the icon from that and paste it to the other two buttons.

Alternatively, you could use the **Main Menu** applet, which condenses the menu bar to a single icon.  The closest thing I can find to a custom menu icon is the **Drawer** applet, but that's basically a panel extension (no labels).

---

### Post by Mazza558 on 2008-03-31
> **aaaantoine said:**
> Find the source code for the **Menu Bar** gnome-panel applet.  You might be able to replace Applications, Places, and System with just icons.  Depending on the type of widget used to create the Applications button, you might be able to just copy the icon from that and paste it to the other two buttons.

Alternatively, you could use the **Main Menu** applet, which condenses the menu bar to a single icon.

The main-menu app is kinda the opposite of what I want - the categories need to be spread out into separate icons.

---

### Post by aaaantoine on 2008-03-31
> **Mazza558 said:**
> The main-menu app is kinda the opposite of what I want - the categories need to be spread out into separate icons.

As noted in a post-facto edit:
The closest thing I can find to a custom menu icon is the **Drawer** applet.  That would give you the ability to spread the menu out into separate icons, but it has the disadvantage of not including labels for each icon.

---

### Post by banjobacon on 2008-03-31
Right click on your Gnome panel and click "Add to panel." 

Click "Application Launcher."

Highlight the application category you'd like to add to the panel.

Click "Add." Now you have a menu for a specific category.

I had no idea this could be done until just right now.

---

### Post by Luffield on 2008-03-31
Here's an idea, not a complete solution, a bit crazy, but I think it would work:
Change you localization files so that instead of Applications, Places and System you'll have A, P and S.

---

### Post by Hells_Dark on 2008-03-31
> **banjobacon said:**
> Right click on your Gnome panel and click "Add to panel." 

Click "Application Launcher."

Highlight the application category you'd like to add to the panel.

Click "Add." Now you have a menu for a specific category.

I had no idea this could be done until just right now.

Great ! :)

---

### Post by Mazza558 on 2008-03-31
> **banjobacon said:**
> Right click on your Gnome panel and click "Add to panel." 

Click "Application Launcher."

Highlight the application category you'd like to add to the panel.

Click "Add." Now you have a menu for a specific category.

I had no idea this could be done until just right now.

Wow, that's a pretty large step... now, is there a way to open these panels on mouse-over?

---

