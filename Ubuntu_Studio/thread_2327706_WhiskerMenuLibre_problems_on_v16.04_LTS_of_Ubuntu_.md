---
title: "Whisker/MenuLibre problems on v16.04 LTS of Ubuntu Studio"
date: 2016-06-13
forum: Ubuntu Studio
---

### Post by yoshii on 2016-06-13
EDIT:  FIXED!  The solution was:  To fix a corrupted Xfce & Whisker menu system, where the categories are missing, remove ~/.config/menus/xfce-applications.menu 
This sets the menu back to the default settings and some of your favorites might still be there too.  Then you can re-add your favorites.  Just DON'T try to edit the menus, it's non-resolved bug.  But at least you'll have your Ubuntu Studio categories back.  

> OK, so everything was OK until I right-clicked on Whisker application menu and selected "Edit Applications" and tried to customize the applications menu.  
Ever since then, it won't show most of my program categories except for stuff like "Office" and "System" and maybe one or two others.  It doesn't show the Audio and Video stuff or some other categories whose names I forget.  

I hunted around my system and the related *.desktop files still exist, but the application menu itself is broken somehow.  Also, my favorites list got shortened to only the Office and System items (none of the audio or video programs are listed).  

If anybody knows how to fix this bug or of a decent workaround, please let me know.  
If there are any other application menu substitutes or application launchers that are lightweight and easy to install I'd be willing to try those.


---

### Post by Dennis N on 2016-06-13
I don't know if this is the case, but sounds like you may have hidden some categories. Each menu category has a "Hide from menus" option with ON/OFF setting.

---

### Post by yoshii on 2016-06-14
Nope, it wasn't hidden categories.  Even trying to hide and then unhide stuff didn't work either.  There's some kind of serious implementation flaw.  I think I read that there have been menu problems with Ubuntu Studio for a long time, even though they changed menu editor programs.  But I found a workaround... see my first post (EDITED now).  

I got my categories back by deleting a certain file.  [http://ubuntuforums.org/showthread.php?t=2327706&p=13503634#post13503634](http://ubuntuforums.org/showthread.php?t=2327706&p=13503634#post13503634)

---

