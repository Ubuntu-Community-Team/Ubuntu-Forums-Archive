---
title: "cannot locate cd rom"
date: 2011-05-29
forum: Wine
---

### Post by arctic_tux on 2011-05-29
Hi,

 have just upgraded to 11.10 from 10.10 and discovered the wine now works (didn't in 10.10 {hardware problems})

anyway i have decided to install age of empires 2 the install ran smoothly but when i go to play it says it cannot locate the Cd-Rom.

it seems to be able to runsome other single file .exe's but most games and large programs (like itunes) say they are always missing something.

I have also tried to run: evil genius and curse of Monkey island with the same results, both need cd's to run.

Compaq Presario
2ghz amd athlon prosessor
32mb S3 prosavage 8 onboard graphics card

---

### Post by cogadh on 2011-05-29
Most of the time, the problem is that Wine does not support all copy protection schemes that use CD checks. Have you checked [Wine's Application Database]("http://appdb.winehq.org/") to see what special configurations/files you might need to use? Additionally, what does Wine's terminal output say when you run into the CD-ROM detection issue?

BTW - iTunes doesn't really work in Wine, so expect a lot of errors when trying to run it.

---

### Post by arctic_tux on 2011-05-29
AOE 2 is rated gold on the app database
how do i see the wine terminal?

thanks

EDIT: oh sorry it actually says :insert **correct** cd rom, not that it cant locate it ,sorry

---

### Post by cogadh on 2011-05-30
Open a terminal (it's under Application > Accessories > Terminal in the "classic" Ubuntu, don't know for sure in the Unity interface, I don't use it), change directories to the game's install directory, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<game install directory>
wine <game executable>.exe
```
Obviously, replace the <game install directory> and <game executable> with the correct info.

---

### Post by arctic_tux on 2011-05-30
the same thing happens as if i had clicked on it in the file browser. "Please insert the correct cd rom press ok and restart the application"

there is no message ore anything in the teminali just get the game loading screen and then the message "ok" closes it.

i have had similar problems with other games that require disks eg cannot find certian file ect.

thanks for your help, do you have any suggestions?

---

### Post by cogadh on 2011-05-30
We were expecting the same thing to happen, we just need to get the terminal output from Wine (we don't really care about errors the game produces, they are mostly meaningless when using Wine). 

It's impossible for there to be nothing in the terminal, Wine can't run without producing some error output; there are normal error messages that always appear, no matter what you are running, plus there should be something that explains why the game can't find the disk. Regardless of whether it appears relevant, copy the content of the terminal to a post so we can review it.

Like I said, its entirely possible that this is simply Wine unable to deal with the copy protection, which is one of the most common problems when running games on Wine, so that could also be the problem with the other games you have tried playing. It's also possible that some files actually are missing. Wine is not complete and only includes the basic functions of the Windows OS, but not any additional support software like Microsoft's .NET infrastructure or the C++ Runtime. Sometimes you may get errors about missing files because you also need to install some required software in Wine. Either way, the terminal output will tell us exactly what is happening.

---

### Post by arctic_tux on 2011-05-30
with all honesty there is no text response within the terminal after I do the: cd ~/.wine/drive_c/Program\ Files/AOE2
wine EMPIRES2.exe

command

this is exactly what appears in the terminal (what i write), nothing appears after i press enter but the the loading screen of the game and the error

> cd ~/.wine/drive_c/Program\ Files/AOE2
wine EMPIRES2.exe
[email]jeremy@ubuntu-DN040A-ABG-S5020AN-AN310:~/.wine[/email]/drive_c/Program Files/AOE2$ 
i can email you a screenshot if you would like

i must be doing something wrong, what do you think

---

### Post by Soulcage on 2011-05-31
Run winecfg, click on drives, click add, set to D:, click ok, click on D:, click browse, then choose the disc (something like /media/QUAKE4_1/

---

### Post by arctic_tux on 2011-05-31
thanks soulcage that got me around the error but after the AOE loading screen has gone nothing else happens. im so confused! i will check the terminal like cogadh suggested before.

EDIT: thanks guys, im going away for a while so no need to reply to this post

---

### Post by arctic_tux on 2011-06-21
i just got this error in the terminal when trying to run the game
> jeremy@ubuntu-DN040A-ABG-S5020AN-AN310:~$ '/home/jeremy/.wine/drive_c/Program Files/AOE2/EMPIRES2.EXE' 
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  1231
  Current serial number in output stream:  1235


---

