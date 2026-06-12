---
title: "Wine installed but no GUI."
date: 2009-02-19
forum: Wine
---

### Post by ikisham on 2009-02-19
Some time ago I installed pptview (powerpoint viewer) and Wine was installed too since it was a pre-requisite. Then I tried, just to fiddle with Wine, some Windows applications but they wouldn't work (SUPER, not really needed, actually states on their site that it wont work with Wine and Google Earth, that didn't work because of my nVidia driver). Then, and this is something that may be corrected in the future, there was at the menu the icons to run the applications and the ones to uninstall them but the correct way to uninstall them was that other option 'unistall Wine applications' or something like that but I only realized that too late so I unistalled the apps but they remained in the menu. Since I couldn't remove that I deleted the 'Wine' menu entrance (maybe I should have just un-ticked) and eventually uninstalled Wine. Now I made my mind to trying it again so I installed it via Add/Remove apps ( wine 1.0.1 and wine-gecko 0.1.0 are installed) but it doesn't show up in the menu so there's no GUI.
How can I get the Wine GUI? Any clues about something in the menu folders that may be wrong?
Thank you and notice that I'm still 'green' with Linux.

---

### Post by cogadh on 2009-02-19
Wine is a terminal application, there is no GUI. There is a GUI for the Wine configuration app and the uninstaller, but for installing applications and just using Wine, there is no GUI at all. There are some third-party GUI front ends for Wine, like Play On Linux and Wine-Doors.

As for your missing menu shortcuts, look for a Wine entry in /home/<user name>/.config/menus/applications.menu. It should have a <Deleted/> on the end of it like this:
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/<username>/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```
Just remove the <Deleted/> and the menu will come back.

---

### Post by ikisham on 2009-02-19
Thanks!That did the trick.
Now my old menu returned with all the entries to 'SUPER' and 'Google Earth' but both were wiped off the system.
* You may answer this only if plain simple since it's by no means a big deal *
Wich file should I edit to remove those entries?
In System>Preferences>MainMenu I can't delete them and just unticking remove most but not all of them.

---

### Post by cogadh on 2009-02-19
Those should be found in the same file as the Wine entry and getting rid of them should just be a matter of removing their "block" of text from the file. Either way, you should still be able to delete anything through the Main Menu editor, you just have to right-click on them and select "Delete".

---

### Post by novafluxx on 2009-03-14
Thank you!! I too lost the menu! LOL

Now I have the old entires back in there too.

Wine was the only thing in the file you mentioned. I removed the deleted line like you said.

Can you tell me why its the only entry in that file, and why deleting it from the menu editor prevents it from returning when I reinstall wine?

---

### Post by cogadh on 2009-03-15
When you delete a sub-menu or shortcut through the menu editor, it doesn't actually delete it, it just appends the menu entry with that </deleted> so that you are no longer shown it in the menu. Unfortunately, reinstalling Wine does not remove that </deleted> flag on its own, so you have to manually fix it. I actually don't delete anything from the menu for this reason. Instead I just un-check it in the menu editor so that it is no longer shown, but if I want it to come back, its just a matter of re-checking it.

As for why it is the only entry in the menu, I honestly don't know.

---

### Post by novafluxx on 2009-03-16
Thank you for the fast reply! I appreciate it!

---

