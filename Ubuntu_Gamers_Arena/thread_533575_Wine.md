---
title: "Wine"
date: 2007-08-24
forum: Ubuntu Gamers Arena
---

### Post by matio on 2007-08-24
Can anyone tell me how to use wine on a cd game!I'm having real trouble installing software from a cd:confused:! Please help!

---

### Post by adewale on 2007-08-24
u can right click it and choose open with wine.

---

### Post by cogadh on 2007-08-24
However, it is strongly recommended that you use Wine through the terminal, that way any error messages from Wine can be output to the terminal. Double-clicking or using the "Open with..." option won't give you that help. Click on the "Stuff I've learned about Wine" link in my sig, the info there will help you get started using Wine.

---

### Post by matio on 2007-08-24
Now i've got another problem! Whenever i try something that worked before it starts it in the menu bar then doesn't launch! It says something like path not found!

---

### Post by mikey5555 on 2007-08-24
codagh,
I'm trying to install Wine so that I may run QuickBooks on my Ubuntu system.  Went to your link "Stuff I've learned about Wine" and followed instructions down to "Install the Wine Gecko IE engine" STEP #3 "Useful Registry Keys" - Here I am confused about the way to enter the information suggested in the "Useful Registry Keys".  My confusion is with the way these changes are presented in the "Tree view".  What is the difference between the following:    **+-sometext**    and **+->sometext**  .  I am not sure which is an entry to the Lefthand Column or the Righthand Column,  Sorta like which is a folder shown in the 'Tree view" of the regisrty in regedit, and which is a "Value or string" belonging in the Righthand column.
I just am not sure how to read the information you presented in "Useful Registry Keys".  Could you clarify this for me, and possibly anyone else needing to use this procedure?  I must be dense or senile....

Regards...
mikey5555
:confused:

---

### Post by cogadh on 2007-08-24
Usually its like this:
**+-sometext** = a registry key (i.e. a folder in the tree)
**+->sometext** = a string value (i.e. something in the right pane)

Basically, when looking at the Useful Registry Keys page, follow the tree down to the last level. Items at that level are all String Values, everything in the levels above them are Registry Keys.

However, QuickBooks is one of those applications that is known to not work in Wine. I don't think anyone has bothered to test it in a while, due to its spectacular failure in the past, so it might be worth trying with the latest Wine, but it will very likely fail to run.

Almost forgot the AppDB reference:
QuickBooks - [http://appdb.winehq.org/appview.php?iAppId=120](http://appdb.winehq.org/appview.php?iAppId=120)
QuickBooks PRO - [http://appdb.winehq.org/appview.php?iAppId=493](http://appdb.winehq.org/appview.php?iAppId=493)

---

### Post by mikey5555 on 2007-08-24
codagh,
Thanks for the clarification about the Registry entries.  Do you know of any other method for  running QB in UBUNTU?  Mabey VMWare...??    My QB version is QuickBooks Pro99 (version 99) if it makes any difference, and I trying to set WINE up to run as Win98 (at least on this 1st try).  

Regards....
mikey5555

---

### Post by cogadh on 2007-08-24
VMWare or some native Linux alternative might be your best bet, but I honestly don't know if there is a comparable native alternative.

---

### Post by mikey5555 on 2007-08-24
cogadh,
Just one mor question....  You instructions say to "Go to the Useful Registry Keys page and scroll down to the HKEY_LOCAL_MACHINE section" but do not mention  "HKEY_CURRENT_USER (a.k.a HKCU)" portion shown at the beginning of this page....  Is this info not needed?  
Thanks for all the help and clarification.

I'm approaching my install and test phase for QuickBooks and I'll let you know my results...
Regards...
mikey5555

---

### Post by cogadh on 2007-08-24
When setting up the Gecko engine in Wine, none of the items in HKCU are required in order to get it running. The only items that matter are the three IE related keys (HLKLM/Microsoft/Internet Explorer/Version, W2KVersion and Build). The rest of the keys may help with other items (I use several of the Direct3D and Alsa Driver items for gaming), but they aren't usually needed for normal Wine use.

---

### Post by mikey5555 on 2007-08-24
cogadh,
It installed, apparently without a hitch, and placed an Icon on the Win Desktop.  Dbl-click QB99 icon, answer some questions, and I'm looking at the "Sample Company Data" for a fictitious company.  I do have one rather glaring problem at this point: My Windows, or wine,  window is much to small, and apparently set to 640X480 (QB asked to be allowed to change this to 800X600 and I said OK), and the "window" is only about 1/3rd of the desktop, thus making me have to scroll Up/DN & Lt/Rt in order ot see the entire QB screen.  I cannot seem to etretch or expand this window to fill my desktop.  Any thoughts on this one??  I think it'll be useable if I can get the Wine Desktop screen to be controllable, ie: Restore/Minimize/Maximize for the Wine Desktop window.

Regards....
mikey5555

---

### Post by cogadh on 2007-08-24
Run winecfg and turn off the "Emulate a virtual desktop" option on the graphics tab. If you really want to keep the virtual desktop setting, then change its resolution to 800x600.

If you have trouble with accessing the buttons on winecfg (because of the small VD) then you can manually edit the registry files. Open the .wine/user.reg file in a text editor, scroll all the way to the bottom of the page and look for an entry that looks something like this:
```
[Software\\Wine\\X11 Driver] 1187989190
"Desktop"="640x480"
```
Change the 640x480 to a minimum of 800x600, but don't set it to be the same size as your actual desktop resolution (makes the VD window too big). You could also delete the whole "Desktop" line and achieve the same results as turning off the Emulate virtual desktop option in winecfg.

---

