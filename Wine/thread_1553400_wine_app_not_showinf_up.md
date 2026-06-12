---
title: "wine app not showinf up"
date: 2010-08-15
forum: Wine
---

### Post by fremantle on 2010-08-15
im using pinguyOS 10.04.01

i recently installed a wine windows application and its not showing up in "wine programs". the only one program i c is notepad. what might be the problem???
im using wine 1.3

---

### Post by murderslastcrow on 2010-08-15
The program isn't showing up in the Wine submenu, or it isn't showing up when you launch it?

You can check the C: drive in the Wine submenu, Program Files, and see if the files actually installed all the way. Otherwise, you may want to refresh your DE's menus by logging out then back in again, killing your panels, or trying to install the program again if it perhaps failed to write those entries the first time (after you try the other steps).

If you still can't find it, go to [http://appdb.winehq.org](http://appdb.winehq.org) and see if the program is compatible with Wine, and how recent the tests were.

You should always check the Application Database before bothering to try installing a program. I don't assume you didn't, of course, just a reminder. Also, it would help if I knew what program you were attempting to install in case it's a bug that needs to be reported.

---

### Post by fremantle on 2010-08-15
utorrent, submenu

---

### Post by ronnielsen1 on 2010-08-15
Bittorent, Ktorrent, deluge, transmission, are some of the native alternatives for utorrent in linux. Utorrent is coming to linux but it's not here yet. I'd recommend installing one of the above packages rather than trying to run utorrent in wine

---

### Post by murderslastcrow on 2010-08-15
Hm, Wine suggests that the installation should go flawlessly, so just try again. I have to do that sometimes if resetting the menus doesn't work (by logging out/in or killing the panels).

But I totally have to agree with Ron, unless it's for study purposes or something really specific to uTorrent, there are dozens of great alternatives on Linux, including Transmission which comes with Ubuntu.

Ktorrent is probably the most similar to uTorrent, although you may have to set up qt to use your Gnome appearance to make it look consistent. But yeah uTorrent's coming to Linux soon anyway. The only different is the applications we've mentioned are open source, while uTorrent isn't. That's one more factor you may want to consider.

---

