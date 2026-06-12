---
title: "how to make tabs"
date: 2007-02-14
forum: Ubuntu System Panel
---

### Post by oliver06 on 2007-02-14
Hello. I saw many screenshots where there are tabs in USP but I can't find where I can configure that.
I installed the svn today and remove my old configuration of USP 0.41 and I would like to know if somebody car explain me how to do or give me a config file for usp.
ps : I can't see System Management too...

thanks

---

### Post by Malac on 2007-02-14
> **oliver06 said:**
> Hello. I saw many screenshots where there are tabs in USP but I can't find where I can configure that.
I installed the svn today and remove my old configuration of USP 0.41 and I would like to know if somebody car explain me how to do or give me a config file for usp.
ps : I can't see System Management too...

thanks
Insert "newtab" (without the quotes) into the plugins list where you would like a tab to start.
To name the tab insert "newtab=[COLOR=DimGray]*what-ever-you-want*[/COLOR]" (without the quotes).
Here is mine:
[ATTACH]25278[/ATTACH]
Which gives me:
[ATTACH]25279[/ATTACH]

Choose "Preferences" from the right-click menu and check that system_management is in the plugins list then check that icon_size and width and height are *not* set to 0.
Try running : ```
usp run-in-window
``` in a terminal and post what the output is.

Hope this helps.

---

### Post by syronth on 2007-02-14
Hi there,

EDIT: Uhm, I'm sorry - I have overlocked that you were talking about USP2. So I guess USP0.41 does NOT have tabs?


[COLOR="Gray"]I was locking for the very same answer, heh. But USP (0.41) says: "plugin newtab=blabla not found". Well - your USPConfig looks also different from what I use here.

Im pretty much confused atm - I just found this nice panel a day ago and ...

> Choose "Preferences" from the right-click menu and check that system_management is in the plugins list then check that icon_size and width and height are not set to 0.

I can't follow you here. USP itself doesn't show "Preferences" in the context menu, only "About". Which right click menu do you mean?

The output after run-in-window shows no errors, just Dir exist, Application added etc.

greetings[/COLOR]

---

### Post by Malac on 2007-02-14
> **syronth said:**
> Hi there,

EDIT: Uhm, I'm sorry - I have overlocked that you were talking about USP2. So I guess USP0.41 does NOT have tabs?


[COLOR=Gray]I was locking for the very same answer, heh. But USP (0.41) says: "plugin newtab=blabla not found". Well - your USPConfig looks also different from what I use here.

Im pretty much confused atm - I just found this nice panel a day ago and ...



I can't follow you here. USP itself doesn't show "Preferences" in the context menu, only "About". Which right click menu do you mean?

The output after run-in-window shows no errors, just Dir exist, Application added etc.

greetings[/COLOR]
Yes, sorry, those features are not available in the 0.41 version.
A deb file and install instructions for USP2 alpha are here:
[http://www.ubuntuforums.org/showpost.php?p=1967430&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1967430&postcount=1)
This is alpha software so you may want to wait until the beta release or full release until you upgrade.
The "Extra" plugins for USP2 alpha are available here:
[http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2)

Hope this helps.

---

### Post by syronth on 2007-02-14
Hi,

thanks a lot. I'm using the current svn now myself to find out how it can crash my whole system ,-) Nah, just playing with it ... and this thing is just looking like an "emacs" for menu management. When will you implement the psychotherapist? C'mon! Can't wait!

Great work so far - time to get stable :-D

greetings

---

