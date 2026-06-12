---
title: "Shadowbane"
date: 2006-03-17
forum: Wine
---

### Post by mgsfan on 2006-03-17
now that its become free to play..I was wondering if anyone ever got it to install on wine..I tried and the installer goes black and it sort of kicks me back to the desktop..and nothing else happens..so hopefully someone has had success..

running lastest release of wine also

---

### Post by dermotti on 2006-03-17
You every try Cedega?

[http://www.transgaming.org](http://www.transgaming.org)

Its free if you compile it from CVS otherwise u can get the binary from transgaming.com ($5 monthly fee)

---

### Post by holobyted on 2006-03-21
I got it running under WINE, but sound was a b... to configure. Seems to have some awful lag spikes when logging into server and opening equipment/inventory/etc windows in-game. (If anyone has any wine-hacks, please share. :p)


I used VMware to extract the game itself and then copied it to my home directory, so I dunno if the installer works w/ wine or not.

---

### Post by wlarsong on 2006-04-22
[QUOTE=holobyted]I got it running under WINE, but sound was a b... to configure. Seems to have some awful lag spikes when logging into server and opening equipment/inventory/etc windows in-game. (If anyone has any wine-hacks, please share. :p)


I used VMware to extract the game itself and then copied it to my home directory, so I dunno if the installer works w/ wine or not.[/QUOTE]

Please inform me as to how you did this.

I installed it on a FAT32 while running windows XP and then copied the directory but when i run it in WINE I get
```
william@ubuntu:~$ wine "c:/program files/SHADOWBANE/sb.exe"
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\program files\\SHADOWBANE\\Core.dll") not found
err:module:import_dll Library Core.dll (which is needed by L"C:\\program files\\SHADOWBANE\\sb.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\program files\\SHADOWBANE\\sb.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\SHADOWBANE\\sb.exe" failed, status c0000135

```

---

### Post by holobyted on 2006-04-22
To be honest, I don't remember 100%. But what I do remember is that I installed it on VMware and ran WINE Shadowbane.exe (not sb.exe)


Had to check several things under winecfg. (ALSA sound, emulation, etc)


Try googling and downloading those .dll's to your SB folder... might be worth a try.

---

### Post by ozelot on 2008-03-11
Its possible to extract the game from the file that extracts from shadowbane.zip.
file-roller didn't work at first. I tried unmass as well but didn't work. strangely now file-roller did work on the exe-file. just extract what you need to a folder within your .wine  drive c. then run
wine shadowbane.exe...(this runs the patcher)
you might miss some fonts. just download and put into yout .wine/drive_c/windows/fonts directory.
also you need to substitute some wine dlls. msvcp60.dll, mfc42.dll and msvcrt.dll in your .wine/drive_c/windows/system32 directory. don't forget to update the settings for the dlls via winecfg(set to native,then... for the mentioned ones)
now the updater should start running through the files. if any file is missing. just create an empty file there and name it as the missing file. the patcher gets the job done then.
having done all this the game itself runs. but still dep. on your luck you might get an extreme amount of "sb.exe errors" that make it impossible to actually play... maybe google for "sb.exe error" before you even start doing all this..

cheers,
oz

---

### Post by ozelot on 2008-03-15
disabling "use occlusion query" via the settings tool SBConfig.exe solved the problems for me.

cheers,
oz

---

