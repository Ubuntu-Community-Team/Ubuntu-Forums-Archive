---
title: "Winetricks problem"
date: 2009-03-12
forum: Wine
---

### Post by ahmednasir91 on 2009-03-12
I am trying to install winetricks but getting an error. Someone please help me.

```
nas@F026:/root$ sh winetricks corefonts dotnet20
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/arial32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Arial.TTF /home/nas/.wine/drive_c/winetrickstmp/Arialbd.TTF /home/nas/.wine/drive_c/winetrickstmp/Arialbi.TTF /home/nas/.wine/drive_c/winetrickstmp/Ariali.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/arialb32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/AriBlk.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/comic32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Comic.TTF /home/nas/.wine/drive_c/winetrickstmp/Comicbd.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/courie32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/cour.ttf /home/nas/.wine/drive_c/winetrickstmp/courbd.ttf /home/nas/.wine/drive_c/winetrickstmp/courbi.ttf /home/nas/.wine/drive_c/winetrickstmp/couri.ttf /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/georgi32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Georgia.TTF /home/nas/.wine/drive_c/winetrickstmp/Georgiab.TTF /home/nas/.wine/drive_c/winetrickstmp/Georgiai.TTF /home/nas/.wine/drive_c/winetrickstmp/Georgiaz.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/impact32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Impact.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/times32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Times.TTF /home/nas/.wine/drive_c/winetrickstmp/Timesbd.TTF /home/nas/.wine/drive_c/winetrickstmp/Timesbi.TTF /home/nas/.wine/drive_c/winetrickstmp/Timesi.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/trebuc32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/trebuc.ttf /home/nas/.wine/drive_c/winetrickstmp/trebucbi.ttf /home/nas/.wine/drive_c/winetrickstmp/trebucit.ttf /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/verdan32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Verdana.TTF /home/nas/.wine/drive_c/winetrickstmp/Verdanab.TTF /home/nas/.wine/drive_c/winetrickstmp/Verdanai.TTF /home/nas/.wine/drive_c/winetrickstmp/Verdanaz.TTF /home/nas/.wine/drive_c/windows/Fonts
Executing cabextract -q --directory=/home/nas/.wine/drive_c/winetrickstmp /home/nas/.winetrickscache/webdin32.exe
Executing cp -f /home/nas/.wine/drive_c/winetrickstmp/Webdings.TTF /home/nas/.wine/drive_c/windows/Fonts
Install of corefonts done
Setting Windows version to win2k
Executing wine regedit /home/nas/.wine/drive_c/winetrickstmp/set-winver.reg
Executing cp -f /home/nas/.winetrickscache/dotnet20/l_intl.nls /home/nas/.wine/drive_c/windows/system32/
Executing wine /home/nas/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Note: command 'wine /home/nas/.winetrickscache/dotnet20/dotnetfx.exe' returned status 43.  Aborting.
```

Thanks

---

