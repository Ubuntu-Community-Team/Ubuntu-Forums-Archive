---
title: "Reinstall Wine -- missing menus and .wine directory"
date: 2010-06-06
forum: Wine
---

### Post by leehach on 2010-06-06
Recently reinstalled Wine and was surprised when [LIST=1]
[*]The Wine menus didn't come back; and
[*]The ~/.wine directory was nowhere to be found.
[/LIST]

Solutions were elsewhere, but scattered around, and somewhat unclear what with the back and forth over what was and wasn't working, so here is the complete no-brainer how to completely remove and reinstall Wine instructions.

Use Synaptic to Mark for Complete Removal [FONT="Courier New"]wine[/FONT] **and [FONT="Courier New"]winbind[/FONT]**, or
```
sudo apt-get remove --purge wine
sudo apt-get autoremove
```

autoremove will remove winbind, while remove --purge will not. 

Delete the  ~/.wine directory and all contents. Remove menus following the instructions from WineHQ: [How do I uninstall Windows applications?]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391") which I repeat here:```
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
```

I also removed the Wine menu folder using the Main Menu system applet, and removed the following code from ~/.config/menus/applications.menu ```
	<Menu>
		<Name>wine-wine</Name>
		<Deleted/>
	</Menu>
```

Reboot Ubuntu.

Reinstall using Synaptic or ```
sudo apt-get install wine
```

Menus should reappear. Several times when I reinstalled I did not get the expected Wine menus. I'm not sure if this was because the menus had previously been incompletely removed, or because previously I hadn't removed winbind with apt-get autoremove.

If there is no ~/.wine directory, don't panic. Just run winecfg, either with Applications&#8594;Wine&#8594;Configure Wine, or just```
winecfg
```. This will recreate ~/.wine.

Thanks to the following:
[http://ubuntuforums.org/showthread.php?t=689564](http://ubuntuforums.org/showthread.php?t=689564)
[http://ubuntuforums.org/showthread.php?t=615827](http://ubuntuforums.org/showthread.php?t=615827)
and of course the folks at WineHQ

---

### Post by cristoslc on 2011-01-30
Thanks, that was *incredibly* helpful.

I had been trying to clean up an Adobe Acrobat X install, but the newly-installed instance (after following all of your instructions) is still failing to open. I'm using exactly the same install procedure that I used the first time -- any idea what might be going wrong?

Thanks!

---

