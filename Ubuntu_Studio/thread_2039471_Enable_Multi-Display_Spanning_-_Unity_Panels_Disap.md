---
title: "Enable Multi-Display Spanning - Unity Panels Disappear"
date: 2012-08-08
forum: Ubuntu Studio
---

### Post by rwheindl on 2012-08-08
I have Ubuntu Studio 12.04 and enabled display spanning across three monitors via Settings -> AMD Catalyst Control Center (Admin) and after reboot, I log in and all Panels are gone, vanished. A huge blank slate of background and nothing else.

I can right click and get a menu, but there are not options to add a panel anywhere. If I open a terminal, is there a command I can run that will restore even just a default panel for me?

Right clicking to do everything is kind of not a cool option so if you have a suggestion, I would really appreciate it. Thanks!

---

### Post by rwheindl on 2012-08-08
Also, the right click menu consists of the following:

- Open in New Window
- Create Launcher...
- Create URL Link...
- Create Folder...
- Create From Template -> Empty File

- Open Terminal Here
- Paste (grayed out)
- Desktop Settings...
- Properties...
- Applications (main menu) -> (Everything else from the main menu here: browser, file manager, gedit, terminal, etc.)

I can't believe they didn't think to include a "Create Panel" option. This used to be on older systems. Any ideas?

---

### Post by rwheindl on 2012-08-08
Holy crap, digging through control panel after control panel, I found it. Here it is for anyone else with this problem:

Right Click -> Applications -> Settings -> Settings Manager -> Panel

Change the Output to "Automatic" and one should appear. Change the dropdown for each panel you wish to restore and set it to "Automatic". Should do the trick.

Previously, before I configured spanning, I had my panels set to show only on display 2, hence they disappeared when I changed the configuration for spanning across monitors.

---

