---
title: "[TUTORIAL]How to install Dungeon Siege II"
date: 2010-03-09
forum: Wine
---

### Post by Fläsh on 2010-03-09
[SIZE=5][B]Pre-Requirements
_______________
[SIZE=2]Ubuntu 9.10 
Wine 1.1.40 (see [/SIZE][/B][/SIZE][SIZE=2][http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)[/SIZE][SIZE=3][SIZE=2][B])
WINETRICKS
[/B]Open a terminal by pressing ALT+F2 and typing 
[/SIZE]gnome-terminal. type 
```
wget http://www.kegel.com/wine/winetricks
```Dungeon Siege II 
+Lastest Patch ([http://download.microsoft.com/download/3/d/c/3dc8d006-dc36-448b-bd0c-469030885fd6/DS2_Patch_2.2.exe](http://download.microsoft.com/download/3/d/c/3dc8d006-dc36-448b-bd0c-469030885fd6/DS2_Patch_2.2.exe))

Creating a wineprefix for ds2 by typing
```
export WINEPREFIX=$HOME/.wine-ds2
```[/SIZE][SIZE=3] in a terimnal.

then type 
```
wineprefixcreate
```after that type ```
winecfg
``` make sure emulation is set to windows xp click audio and set it to oss drivers. Your done with creating a bottle for the game.


[SIZE=7][SIZE=5]Installing The Game
________________
1.[SIZE=3]Insert the first disc labled ´Disc 1´ 
2.Once it mounts open a terminal window by holding ALT+F2 and typing gnome-terminal.
-Type ```
cd /media/cdrom/ then type wine setup.exe
```3. Follow the on-screen instructions and when it asks for Disc 2 through 4 type this ```
wine eject
``` insert the next disc wait for it to mount then hit ok. 

3.After installing it apply the patch you have downloaded earlier.

4. Once you´ve applyed the 2.2 patch to your install your done with ds2 for now.

5.Open a terminal window by pressing and holding ALT+F2 till a run window pops up type gnome-terminal
Type ```
sh winetricks allfonts d3dx9 msxml6 vs2005express directplay riched20
```Winetricks should do its job and install the packages type in.

6.Close the terminal window.

7.Play the game by going to Applications->Wine->Programs->Dungeon Siege II  
[/SIZE]
Its not working !
______________
[/SIZE] [/SIZE] 
You get the error messages.
refer to ([/SIZE][http://appdb.winehq.org/objectManager.php?sClass=version&iId=4315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4315)) 

[SIZE=3]I can´t play online
refer to ([/SIZE][http://wiki.winehq.org/DirectPlayGames](http://wiki.winehq.org/DirectPlayGames))

---

### Post by jwhiz on 2010-06-08
Hi;

Can't get past first disk.

Did the "wine eject", which ejected CD #1. CD #2 wouldn't mount, tried many things including pmount. After several minutes, I popped out CD 2 and popped it back in, it then automatically mounted. However, the installer wouldn't recognize it. I tried going through the Wine explorer to the setup file on wine "c" drive, got a popup window asking for disk 2 - also not recognizing disk in drive.

Help?

---

### Post by Lancro on 2010-12-06
In the first cd, after you put the serial, it displays the message, pidgen.dll not available, check if cd1 is inserted, and yes, its inserted and with the dll, if I put the dll on wine (we are talking about wine 1.2.1 and maverick) it closes with an error message, anyone know how to fix it?.

Thanks.

---

### Post by Lancro on 2010-12-09
Ok I solved that issue, now I have another, if I try to play fullscreen, the mouse cursor dont go up, Its always down, it moves from side to side, but it doesnt go up, so I have to play it in a virtual desktop, anyone knows a fix for fullscreen mode?.

Thanks.

---

