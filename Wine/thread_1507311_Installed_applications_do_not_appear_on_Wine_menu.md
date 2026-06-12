---
title: "Installed applications do not appear on Wine menu"
date: 2010-06-11
forum: Wine
---

### Post by Zenith88 on 2010-06-11
Just installed several apps including Firefox for example, but Wine programs menu still has just Accessories-Notepad.

How do I launch the installed apps?

Also, Firefox launched itself after install and I selected to use it as default browser. Now that I start Cisco SDM it opens Wine IE window, which is blank and has a horizontal separator at the bottom which can be dragged up and down, but nothing else happens. Java was installed, so it should not be a problem - SDM would not let me install it if Java was not there.

IE when launched separately has no main menu and does not seem to be able to open dialogues such as page properties.

Wine configuration tool does not save configuration even though the reg files get timestamp updated.
But when I press Check Now in Firefox/Always check... setting, .reg files do not get updated and Wine does not use Firefox as default browser.

Tried installing IE8, but its window is corrupt and it can't connect to the Internet.

What am I doing wrong?

---

### Post by cogadh on 2010-06-11
The only thing you are really doing wrong is installing IE8. Almost none of the "real" IE versions will work in Wine, especially IE 7+. Wine's own implementation of IE is not really a functional browser, its really just the basic framework for some apps that may use IE components or check for the presence of IE at install.

The reg thing sounds like a simple permission issue, as in you don't have permissions to write to the files in the .wine directory. I would verify that first and fix any permissions that might be off, then try Firefox again.

EDIT - Forgot about the menu issue and launching apps without it. Any apps installed with Wine should automagically appear under the Wine menu, unless you had previously installed, removed and then manually deleted the shortcuts for that app. If you have done this, run the menu editor (System > Preferences > Main Menu) and check for the presence of hidden shortcuts. If there are none, then we may have to get into manually editing some files or manually creating shortcuts. In the meantime, you can run the app either from the terminal ("wine ~/.wine/drive_c/<path to executable>/<app name>.exe") or use the "Browse C: Drive" shortcut to find the executable in the file browser and run it by double-clicking it.

---

### Post by Zenith88 on 2010-06-12
> **cogadh said:**
> The reg thing sounds like a simple permission issue, as in you don't have permissions to write to the files in the .wine directory.

Can't be permission issue - the files do get updated. Just not with the info I indicated above.

---

