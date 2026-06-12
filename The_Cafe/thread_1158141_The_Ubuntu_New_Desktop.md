---
title: "The Ubuntu New Desktop"
date: 2009-05-13
forum: The Cafe
---

### Post by dael99 on 2009-05-13
Karmic needs a UI redesign, not only a cute theme.

By now, Gnome is copying various Windows features, like having a taskbar with context-menu actions, a button based taskmanager at the bottom, etc.

What i mean is not that we should use others features because they are already in used, i mean making a real chage in the User Interaction experience.

Right now, screen are getting wider and wider, so we lost valuable height. Gnome pannels, use 46px in the screen and valuable space is wasted at the right of the Application titlebar.

To make Karmic REALLY unique, i propose 4 changes:

1) Replace the main menu words (apps, places, system) by icons.
By the time, this can be more intuitive to the user, instead of reading words that may vary in their regions, for example "Programas" "Aplicaciones" or "Ejecutables" are used in Spanish to reference applications.

2) Add a iconified task-manager
Reuse existing launchers in the panel and use them as we currently use the buutons in the taskmanager. Also, would be GREAT to replace the context-menu icons of the system tray, adding those menus to the context-menu of the icons in the taskmanager/launcher.
This could replace the need for 2 panels, leaving only one. Also, is very artificial that users need to have one icon in the pannel for a custom launcher, one button in the bottom for the application switching and ANOTHER icon in the system tray for custom context-menu actions. This could be more intuitive.

3) Force apps to use tabs and GDI-like windows, maybe pannels.
Applications like openoffice.org, Dia, GIMP, and many others uses more than one window to operate, so if i'm opening only one image why should i have 3 items in the tasklist? or why openoffice uses a new window for every document if , as user, I am used to the tabs in nautilus and firefox, also a simpler app like Gedit is using tabs. This way we could have the titlebar clean, showing only the app name, deferring the title of the document to the tab text.

4) Reuse the titlebar.
Right now, apps with a short name are wasting precious pixels al the right of their titlebar. I propose, to have a unique Ui and reuse that space, add the main menus to the aplication main titlebar.
So, if the document title is visible trough the tab text, we have a clean titlebar, and we can put menus on it.
To move the windows, click on the name. And if the menus are too much, reuse the GIMP system, of adding a sub-menu for all that does'n fit there.

MOCKUPS: [http://picasaweb.google.com/dael99/Mockups](http://picasaweb.google.com/dael99/Mockups)

Best Regards.

P.D.: Windows has already deleted the titlebar and the menubar on their apps, Mac has that GlobalMenu, so, what do we have?

---

### Post by Mr. Picklesworth on 2009-05-13
There is a pretty heavy UI redesign in the workings for GNOME 3.0, which will probably be the 2.30 release (with Ubuntu 10.04). And yes, the window list is being rethought with it in mind that window lists were simply cruft tacked on to compensate for window managers being useless, and can be eradicated entirely in all shapes and forms if it is just intuitive to organize windows in the first place, with the tool actually intended to do the job (the window manager).

So your wish has been granted :)


Disagreed about tabbed MDI. GNOME is mostly opposed to that idea, for good reason; organizing multiple windows of an application is the window manager's job, and arbitrarily using tabs is just silly especially when not all applications support it (which we can never guarantee). There is a Google SOC project to get applications providing info about open documents in tabs, so perhaps it will be less painful in 6 months and I will be less bothered by the matter.
Now that doesn't mean I don't like tabs (as in the notebook widget). My favourite example of tabs used well is an application called Reinteract. One likely has a single smallish project, with many worksheets. Worksheets for that project are all displayed in tabs. New project (called a notebook in its case): New window.
Gaphor *should* do something similar; it displays different diagrams for a document in tabs.

As for merging stuff into the titlebar, the big issue is that it's just not feasible from a technical perspective. GTK was designed with menu bars just being generic widgets that you throw onto a window, wherever you please. We can never guarantee that a menu is actually meant to be the main menu for a window or even makes sense at the top of it. (Hence GlobalMenu for GNOME, while cool, being a bit hackish). Getting that working would require either rethinking window menus in GTK or (probably better) implementing a special "window title bar" container that can be added to by GTK apps.
Either way, we then face the issue that the window manager must support the magic, which will anger Compiz people tremendously.

Your mockups there are nice, but I don't see how people can drag those windows in the current incarnation. Need some space beside the menus at least ;)

Personally, I think window frames should remain entirely detached from applications, but could do with being spiced up by non-essential extensions. Windows has a system in place where applications can add buttons to window titles, and I think it would make a lot of sense here, too. For example, with audio events attached to windows, we could have volume control widgets on windows themselves which would make a lot of sense.
A framework could be produced to say "this document, with this icon and this description text is open in this window," allowing another system to add a draggable document info box somewhere, furthering the "document is presented in a toplevel window" metaphor. I'm thinking this would be a good way to represent settings, so one could open a settings dialog then drag / drop the window's document icon to back them up.

---

### Post by SunnyRabbiera on 2009-05-13
> 1) Replace the main menu words (apps, places, system) by icons.
By the time, this can be more intuitive to the user, instead of reading words that may vary in their regions, for example "Programas" "Aplicaciones" or "Ejecutables" are used in Spanish to reference applications.
I believe something like this is set for Gnome 3, but it wont show up in Gnome 2.

> 2) Add a iconified task-manager
Reuse existing launchers in the panel and use them as we currently use the buutons in the taskmanager. Also, would be GREAT to replace the context-menu icons of the system tray, adding those menus to the context-menu of the icons in the taskmanager/launcher.
This could replace the need for 2 panels, leaving only one. Also, is very artificial that users need to have one icon in the pannel for a custom launcher, one button in the bottom for the application switching and ANOTHER icon in the system tray for custom context-menu actions. This could be more intuitive.
I dont think this will happen, this is more of an issue with Gnome then Ubuntu itself.

> 
3) Force apps to use tabs and GDI-like windows, maybe pannels.
Applications like openoffice.org, Dia, GIMP, and many others uses more than one window to operate, so if i'm opening only one image why should i have 3 items in the tasklist? or why openoffice uses a new window for every document if , as user, I am used to the tabs in nautilus and firefox, also a simpler app like Gedit is using tabs. This way we could have the titlebar clean, showing only the app name, deferring the title of the document to the tab text.
You canyt force apps to do anything, Ubuntu does not make the apps you see and I doubt someone will come in and force people to use the same UI like Microsoft does.

> 
4) Reuse the titlebar.
Right now, apps with a short name are wasting precious pixels al the right of their titlebar. I propose, to have a unique Ui and reuse that space, add the main menus to the aplication main titlebar.
So, if the document title is visible trough the tab text, we have a clean titlebar, and we can put menus on it.
To move the windows, click on the name. And if the menus are too much, reuse the GIMP system, of adding a sub-menu for all that does'n fit there.

Er what?

Anyhow most of this is more of a gnome issue then a Ubuntu one, if you dont like it try KDE...
KDE4 is still very experimental though

---

### Post by dael99 on 2009-05-13
> **SunnyRabbiera said:**
> I believe something like this is set for Gnome 3, but it wont show up in Gnome 2.

Nice...

> **SunnyRabbiera said:**
> I dont think this will happen, this is more of an issue with Gnome then Ubuntu itself.

i don't think that is being an gnome issue, in fact, there IS an applet called dockbarX, and adds a lot of sense when using aaplications. So, implementing an applet is not a gnome issue, is more like a decisson that "we" have to take.

[http://www.gnome-look.org/content/show.php/DockbarX?content=101604](http://www.gnome-look.org/content/show.php/DockbarX?content=101604)


> **SunnyRabbiera said:**
> You canyt force apps to do anything, Ubuntu does not make the apps you see and I doubt someone will come in and force people to use the same UI like Microsoft does.

I totally agrre with that. I don't mean to force a development team to do something, but if we try to develop something in a collective way, we could get a more homogeneous interface, compare Dia, Inkscape, Scribus and other related apps, they all differ in the way of interacting to the User. ONE BIG exaple of this, are the shortcut.

Also, for Nautilus, it's called Filemanager and Nautilus in different places.



So, why i think we should show the real name of an app in the titlebar?
Because, when we install update and see the packages, we don't see Filemanager in any packagename (ok, in the description, i know). So, i think we should show only the REAL app name in the titlebar (along with the menus) because users need to know what app they are using, Madia Player, ok, but give it a name.....

Er what?
> 
Anyhow most of this is more of a gnome issue then a Ubuntu one, if you dont like it try KDE...
KDE4 is still very experimental though

and no, i don't like Windows-like desktops.

---

