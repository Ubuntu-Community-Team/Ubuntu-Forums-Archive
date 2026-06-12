---
title: "How to completely remove Wine"
date: 2010-06-27
forum: Wine
---

### Post by ALIENDUDE5300 on 2010-06-27
Ok, so I was having trouble with wine -- it was starting up slow, and I decided I just wanted to delete everything in it and start over. After a while, I figured out how to do that, and I'm posting this here in case anyone else needs to do the same. Hopefully, someone will find this useful.
```
wineserver -k
sudo apt-get remove --purge wine wine1.2 winetricks -y -f
rm -rf $HOME/.wine
rm -rf $HOME/.winetrickscache
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```
To reinstall wine, run:
```
sudo apt-get install wine1.2
```
**This will delete EVERYTHING in your Wine installation. Make sure you don't have anything you care about in there before doing this.**

---

### Post by hikaricore on 2010-06-27
Honestly your apt-get command should do the trick for everything.
Completely removing the .wine directory after doing this is pretty much redundant. (and possibly others)

---

### Post by cogadh on 2010-06-28
Actually, the .wine directory is left behind and so is the .winetricache (if you actually used winetricks in the first place), but all that stuff about removing the menus and shortcuts should be completely unnecessary. Also, specifying the "wine1.2" package is unnecessary. Both the uninstall and install commands only need "wine" to function. For example, "sudo apt-get install wine" will always give you the latest version available from the repositories. If you have added the WineHQ repository, that means you will currently get one of the 1.2 release candidates; if you only have the Ubuntu repositories, that means you will only get 1.0.1.

---

### Post by hikaricore on 2010-06-28
If the .wine directory is left behind during a --purge then something is wrong..

---

### Post by ALIENDUDE5300 on 2010-06-28
> **cogadh said:**
> Actually, the .wine directory is left behind and so is the .winetricache (if you actually used winetricks in the first place), but all that stuff about removing the menus and shortcuts should be completely unnecessary. Also, specifying the "wine1.2" package is unnecessary. Both the uninstall and install commands only need "wine" to function. For example, "sudo apt-get install wine" will always give you the latest version available from the repositories. If you have added the WineHQ repository, that means you will currently get one of the 1.2 release candidates; if you only have the Ubuntu repositories, that means you will only get 1.0.1.

if you have the wine ppa installed, winetricks is now automatically installed with wine1.2. That's why I included that command in there. The stuff about menus and shortcuts is totally useful to me, as I hate the clutter of having programs I don't have installed listed in the menus. I wanted to start from a fresh slate.

---

### Post by ALIENDUDE5300 on 2010-06-28
> **hikaricore said:**
> If the .wine directory is left behind during a --purge then something is wrong..

I tried a purge, but that was insufficient. These commands pretty much guarantee that everything related to wine is completely deleted.

---

### Post by hikaricore on 2010-06-28
The entire purpose behind purge is to remove the application completely including all the data it installed or created.
Unless something has changed recently..

---

### Post by cogadh on 2010-06-28
> **ALIENDUDE5300 said:**
> if you have the wine ppa installed, winetricks is now automatically installed with wine1.2. That's why I included that command in there. The stuff about menus and shortcuts is totally useful to me, as I hate the clutter of having programs I don't have installed listed in the menus. I wanted to start from a fresh slate.
Winetricks is also installed if you just run "sudo apt-get install wine" with the PPA enabled (that is the WineHQ repository), but that doesn't create the .winetrickscache directory, it is only created when you actually use the winetricks script (just like the .wine directory is only created when you actually use Wine). All that shortcut stuff should get removed when you uninstall Wine, if it isn't, then hikaricore is right, there is something wrong with what the --purge is doing.

---

### Post by rtimai on 2010-08-22
It's been a while since the last post, but for the record, ALIENDUDE5300 is right, at least in my own experience. The winetrickscache contents are not removed when purging wine or winetricks because they are not recorded in the apt-get history, but downloaded and installed by winetricks, which is a shell script. The winetricks script installation itself is a single file copy, and that's all that's removed when uninstalling winetricks. 

WineHQ acknowledges that the application menu items are not removed when uninstalling the Windows applications. The instructions for removing wine application menu items that ALIENDUDE5300 gave are from the WineFAQ:

> [http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391](http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391)

The ~/.wine directory does not contain the wine installation, but is what wine calls the wineprefix, which contains the Windows application installations and configuration files. When a Windows application fails to work in wine, the standard "undo" is to delete the .wine directory, which purges the wine *application* installations. Then running winecfg re-initializes wine, causing it to "forget" the previous Windows application installations. You are effectively then re-starting from scratch with wine intact, and no Windows applications, except "fakeie" that comes with wine 1.2+.

FWIW...

---

### Post by PS8 on 2010-10-19
This is really helpful. I had the wine folder I purged wine and this commands helped remove everything. Thanks mate.

---

### Post by Articseabear on 2010-12-21
I've never had to purge before, this was helpful for me to clear the folder in applications. Thanks :p

---

### Post by isalovell on 2012-06-07
I tried all of the commands but Wine was still there in the Applications menu :(

---

### Post by kdane4 on 2012-06-07
> **isalovell said:**
> I tried all of the commands but Wine was still there in the Applications menu :(

Hi isalovell,

It probably didn't work as this thread is old.. I suggest you create a new one. 

cheers!! ;)

---

### Post by lisati on 2012-06-07
> **kdane4 said:**
> Hi isalovell,

It probably didn't work as this thread is old.. I suggest you create a new one. 

cheers!! ;)

True: a lot has changed in the last couple of years.

*Thread closed.*

---

### Post by Elfy on 2012-06-07
Old thread closed.

---

### Post by lisati on 2012-06-07
> **elfy said:**
> old thread closed.

Hello! :D

---

