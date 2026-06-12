---
title: "Wine - The Edge of Despair"
date: 2010-08-23
forum: Wine
---

### Post by DavidOfLondon on 2010-08-23
Firstly, I iust started using ubuntu and I love it. I thought I'd try out wine to play BF2 and it didn't work...screen went black. 

I just want to completely remove the installed files but Wine won't do it - can't handle even the uninstall prog. I am driving myself insane trying to locate where it's sent the files.

Can I just delete them all and trust that there won't be any issues?

My laptop is powerful enough - 2ghz, 1gb ram etc, so it's not the hardware.

I just want to remove all the installed components whether by force or elegance.

If you can help me, I'll say a Hail Mary for you.

I just don't understand where linux saves files.... I'm a total noob but it seems much easier to find something in windows and just zap it. I know - I just spoke words of heresy.

Mea culpa, mea culpa, mea maxima culpa.

---

### Post by JBAlaska on 2010-08-23
Wine installs programs in ~/.wine/drive_c/Program Files

---

### Post by DavidOfLondon on 2010-08-23
Yeah, I had that part of the puzzle to hand but I have no clue at all how to look for that folder. All I see in the explorer is root, file system, yaddah yaddah etc. 

The search function won't find the wine folder for me (it'll find 4 of them but not the one I need) and I am growing ever more tempted to go back to windows.

I'm clearly committing a basic error but the problem I see a lot with Linux is the assumption of knowledge on the new user's part which clearly doesn't exist.

This is the same as learning an entirely new language and I must confess it *is* phasing me now.

> **JBAlaska said:**
> Wine installs programs in ~/.wine/drive_c/Program Files

---

### Post by JBAlaska on 2010-08-23
Click on **Places, Home Folder**
That will open Nautilus viewing your **~/** (**home**) folder
Click on **View, Show hidden files** (The . before .wine makes it hidden)
Double click on **.wine, drive_c, Program Files**

Your windows program install should be there.

Hope this helps, and hang in there, Linux gets easier as you do more tasks and start to understand how it works "under the hood".


As far as BF2, I've never tried it, but check out [WineHQ](http://appdb.winehq.org/appview.php?iVersionId=3438) for your WINE version and version of BF2.

---

### Post by DavidOfLondon on 2010-08-23
I REALLY appreciate this.

I have a crappy old laptop I can use for playing poker and BF2 etc until ubuntu/linux finds a way to deal with the Goliath that is Evilsoft. Inc.

I've managed to completely remove the components now so I'm very grateful.

What I love most about linux is that everything is an option and if you screw up there is an entire community to offer help. I love the concept - work together, produce good stuff, give it to others for free! In such a crappy world I must say I find all this very impressive.

As long as I can write a document, send and email, and watch a video, I don't mind. The rest can be done on the Ye Olde Laptoppe.

:)

Peace,

David.

> **JBAlaska said:**
> Click on **Places, Home Folder**
That will open Nautilus viewing your **~/** (**home**) folder
Click on **View, Show hidden files** (The . before .wine makes it hidden)
Double click on **.wine, drive_c, Program Files**

Your windows program install should be there.

Hope this helps, and hang in there, Linux gets easier as you do more tasks and start to understand how it works "under the hood".


As far as BF2, I've never tried it, but check out [WineHQ]("http://appdb.winehq.org/appview.php?iVersionId=3438") for your WINE version and version of BF2.

---

### Post by JBAlaska on 2010-08-24
Glad that helped.

If you want to get rid of the shortcut entry(s) in **Applications, Wine, Programs** Right click on **Applications** and select **Edit Menus** find the entry(s) you want and delete.

---

### Post by xx58 on 2010-10-11
Click Application, then Wine, then Browse C drive, then Programs File and then Delet all Folder what you don't like. Easy??? Then do it!

---

### Post by aspiredfang on 2010-10-11
I know this has been resolved but figured I would throw in a couple of cents about finding WINE. Another way is quite simply:

- Open up your file manager so that it is in your home directory
- Press <ctrl> + H. This will temporarily show any hidden items
- double click on .wine

You are now in the WINE "file system"

---

