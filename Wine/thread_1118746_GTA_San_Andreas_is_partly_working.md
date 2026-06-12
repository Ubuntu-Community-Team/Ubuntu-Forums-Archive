---
title: "GTA San Andreas is partly working"
date: 2009-04-07
forum: Wine
---

### Post by stardustdk on 2009-04-07
Hey all.

Installing GTA San Andreas is working.

Under Wine - Browse C:\drive, I can get to the directory in which the game is - and start GTA - so far so good... :neutral:

What i DON'T get working is:


No icons, even though I asked for it during installation?! :(

Want a Symbolic link from the gta_sa.exe working on the Desktop, preferred with an icon.

Have searched for suggestions, but none is working. :(


Best regards

Stardustdk

---

### Post by stardustdk on 2009-04-07
I know this. It is not possible the way you describe. It is in the hidden .wine dir. And the icons I can't find anywhere. Tried making the link with "wine .wine/drive_c/Program Files/...."  as I found in a howto - it didn't work :(. 

Help is still wanted.

Best regards

---

### Post by jnewl on 2009-04-07
The command line for your launcher needs to follow this form (you'll have to put in the correct directory/file names; I just guessed):


env WINEPREFIX="/home/stardustdk/.wine" wine "C:\Program Files\Rockstar Games\GTA San Andreas\GTASA.exe"


EDIT: In addition, if you want to use the game's own icon, it's a little confusing how to do it. First of all, when you bring up the dialog box to find your icon, you need to realize that the list doesn't update automatically. You have to scroll to the directory you think has the icon in it and then hit Open. It will then look for icons in that directory. In addition, I think it only accepts icons in .PNG format. My memory is hazy on that, but you'll find out soon enough when you try it.

---

