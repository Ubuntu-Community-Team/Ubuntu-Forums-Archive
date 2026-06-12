---
title: "How do you remove your current install of Wine without removing the games?"
date: 2009-09-16
forum: Wine
---

### Post by Leopardson on 2009-09-16
Hi, I installed Fallout 3 (Steam, not retail) with Wine.
After struggling with Xlive keeping the game from starting, I murdered Xlive with <a href="http://www.fallout3nexus.com/downloads/file.php?id=1086>this random program.</a>
Now, whenever I start a new game (Buggy mouse, too), my computer locks up like a bank safe during a massive prison break riot on a holiday.

I now realize I had skipped a very important step of compiling a special wine found at the winehq site.

It took me 12 hours to download that game, plus another 48 for all the other steam games I have uninstalled, so I don't want to remove my wine games. (My internet is almost as fast as a mortally wounded turtle-snail hybrid in the middle of Death Valley.)

Is there a way I can uninstall my current version of Wine (1.1.29) without uninstalling the games OR overwrite the current wine install with a new one?

Also, if I installed Fallout 3 with a different wine, should the D3d patch on a new wine still work?

---

### Post by snova on 2009-09-16
> **Leopardson said:**
> Hi, I installed Fallout 3 (Steam, not retail) with Wine.
After struggling with Xlive keeping the game from starting, I murdered Xlive with <a href="http://www.fallout3nexus.com/downloads/file.php?id=1086>this random program.</a>
Now, whenever I start a new game (Buggy mouse, too), my computer locks up like a bank safe during a massive prison break riot on a holiday.

I now realize I had skipped a very important step of compiling a special wine found at the winehq site.

What is that?

> It took me 12 hours to download that game, plus another 48 for all the other steam games I have uninstalled, so I don't want to remove my wine games. (My internet is almost as fast as a mortally wounded turtle-snail hybrid in the middle of Death Valley.)

Is there a way I can uninstall my current version of Wine (1.1.29) without uninstalling the games OR overwrite the current wine install with a new one?

The installation of Wine is separate from the place it installs Windows programs (the ~/.wine directory). Uninstalling it the usual way will not affect it.

> Also, if I installed Fallout 3 with a different wine, should the D3d patch on a new wine still work?

Not sure. If the patch was something that modified files in ~/.wine, then it will still be there at any rate- but I wouldn't know whether it might stop working. I suspect not.

---

### Post by Duskao on 2009-09-16
Save yourself alot of pain and suffering. Either figure out how to create different wine prefix's or use POL. As far as I know, it is not possible to uninstall wine without deleting your games. The only way I can think of is to manually grab the folders out of your wine folder and put them somewhere else on your computer, or on a flash drive or something along those lines. 

You are much better creating different prefixes in case something like that happens, then you can configure wine for each prefix and if you screw up you can just delete that prefix without causing any other issues to wine or your other games. 

Since you are trying to install Fallout 3, I would strongly suggest downloading and install Playonlinux from playonlinux.com as it will automatically create a new prefix for each game and for the scripts in their repository (there is one for fallout 3) it will configure the prefix especially for that game. Also for other games that are not in the repository you can manually configure the prefix. Make sure you get the "advanced configuration plugin" for POL on the POL web page to help you out when configuring. 

Best of luck with all that.

---

### Post by Leopardson on 2009-09-16
> Since you are trying to install Fallout 3, I would strongly suggest downloading and install Playonlinux from playonlinux.com as it will automatically create a new prefix for each game and for the scripts in their repository (there is one for fallout 3) it will configure the prefix especially for that game. Also for other games that are not in the repository you can manually configure the prefix. Make sure you get the "advanced configuration plugin" for POL on the POL web page to help you out when configuring.

Umm...

> Fallout 3 (Steam, not retail)
> It took me 12 hours to download that game, plus another 48 for all the other steam games I have uninstalled, so I don't want to remove my wine games. (My internet is almost as fast as a mortally wounded turtle-snail hybrid in the middle of Death Valley.)

Thanks for the post, but I already have POL and tried to install Fo3 through it first. It asked me for a DVD path.

> The installation of Wine is separate from the place it installs Windows programs (the ~/.wine directory). Uninstalling it the usual way will not affect it.

Would you mind telling me the usual way, then?

---

### Post by snova on 2009-09-16
> **Leopardson said:**
> Would you mind telling me the usual way, then?

How did you install it? The usual way would be through Synaptic (possibly with additional repositories enabled, but it works the same way), in which case it can be removed with the same program.

---

### Post by por100pre1 on 2009-09-16
Just rename your .wine folder, run **Configure Wine** and then copy the ~/.wine/drive_c/Program Files/Steam folder to the new folder.

---

### Post by Leopardson on 2009-09-16
>  			 			 			 		   		 		 		Just rename your .wine folder, run **Configure Wine** and then copy the ~/.wine/drive_c/Program Files/Steam folder to the new folder.
Apparently, uninstalling Wine through Synaptic as Snova suggested doesn't kill your installed stuff.


> Since you are trying to install Fallout 3, I would strongly suggest downloading and install Playonlinux from playonlinux.com as it will automatically create a new prefix for each game and for the scripts in their repository (there is one for fallout 3) it will configure the prefix especially for that game. Also for other games that are not in the repository you can manually configure the prefix. Make sure you get the "advanced configuration plugin" for POL on the POL web page to help you out when configuring.O.K, apparently my PlayOnLinux was the same version Galileo used to run his brand new telescope. I updated it and, apparently there is an "Adapt from steam option".

I installed Steam through PlayOnLinux assuming it would detect the steam folder, then clicked the "Adapt from Steam" option, expecting it also to detect the previous folder.

Instead, I got a completely different copy of steam and a useless Fallout 3 menu option that links to nothing.

Is there a way (Maybe changing wine prefixes or something) I can make PlayOnLinux use the real Steam and the real Fallout 3?

Also, is there a way to either run any wine program from PlayOnLinux or rob the 1.1.29-Fallout wine version?

---

