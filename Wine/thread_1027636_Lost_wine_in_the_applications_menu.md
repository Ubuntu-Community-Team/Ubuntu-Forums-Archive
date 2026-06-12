---
title: "Lost wine in the applications menu"
date: 2009-01-01
forum: Wine
---

### Post by Arunomi on 2009-01-01
I hade problems with wine so i uninstalled and reinstalled wine
but in the process all wine stuff in the application menu just disapperd.

And i find it a little hard to work with wine now.

So how do i get them back?

Pleas help.

---

### Post by hikaricore on 2009-01-01
This functionality is still experimental in WINE if i recall, you'll just need to add the items manually if I'm not mistaken.

---

### Post by matteojg on 2009-01-01
I have the same problem. Not only did wine vanish from my app menu but it no longer showed up as an 'open with' option initially when  i right clicked a file (not even under the 'other' menu). 

I understand it is a bug, so we will just have to wait for a fix.

In the meantime you can use the terminal to run programs with wine, or right click the file you wish to open, select 'open with other application', then select 'use custom command' at the bottom of the window and type in 'wine'...this worked for me and also added 'wine' to the list of applications to open the file after right clicking on it.

I tried manually adding a launcher to my desktop but kept receiving a 'permission denied' error and from what i gather using root and/or sudo commands with wine is a huge no-no so I let that be.

(using last stable build of wine [1.0.1] and Ubuntu 8.10)

---

### Post by matteojg on 2009-01-02
OK, I think I found a fix for this (thanks to the wineHQ documentation):

1. Go to your home folder (Places>Home Folder)
2. Open the 'view' menu and select 'show hidden files'
3. You should now see a folder named '.config', open this folder.
4. Open the folder named 'menus'
5. Open the 'applications.menu' file, this should open what appears to be a .html document.In this document you should see the following entry:

<Menu>
		<Name>wine-wine</Name>
		<deleted/>
	</Menu>
6. Remove the <deleted/>
7. Select 'Save'
8. Open the Applications menu, and you should see a little glass of wine again (i hope).

(see 6.28 in the official wine wiki [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ))

---

### Post by soluphobe on 2009-01-02
Also, you've probably heard this, but reinstalling wine doesn't actually do anything.  All your programs and configurations are kept in a hidden folder (called .wine) inside your home directory - to really reinstall wine you have to get rid of that folder.

---

