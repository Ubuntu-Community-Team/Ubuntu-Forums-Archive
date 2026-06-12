---
title: "wine: could not load L&quot;C:\\windows\\system32\\program]#.exe&quot;: Module not found"
date: 2008-12-09
forum: Wine
---

### Post by jdc.84 on 2008-12-09
Wine 1.0.1 installed today.

I installed wine but i cannot see it in the Applications menu. When i try to add in 'Edit Menus' it can't be seen anywhere.



I had a look through previous threads and found: winecfg. Typing winecfg does load the config window but with the following error msg:

"
john@john-desktop:~$ winecfg
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
"



When i try to load the program from terminal i get the following:

"
wine: could not load L"C:\\windows\\system32\\program]#.exe": Module not found
"

Does this mean that the installation of the program came a cropper somewhere along the line? If so what i the safest way of removing Wine 1.0.1 and trying again?

Any help would be much appreciated.

---

### Post by hikaricore on 2008-12-09
Either your installation is borked, or you are doing something wrong.  Run:
> sudo apt-get remove --purge wine
Then reinstall WINE.

I'm not sure what you're expecting to find in the applications menu aside from
winecfg and a few other small programs.  WINE is not an application launcher by
and means, but something that applications are launched upon.

After you've installed whatever program you would like to run under WINE go to
it's installation directory and test it from the console there first before trying
any icons it may have created.  For example:

> cd ~/.wine/drive_c/Program\ Files/Photoshop/
wine photoshop.exe

You may see some fixme messages but these are not errors, if the software loads up
from here go ahead and exit it then test any desktop or menu items WINE may have
created for said software.  This way you can be sure it runs before aimlessly
clicking around your desktop.  ^_^

Please try to be as specific as possible when posting for help here, I'm not 100%
sure as to what you were saying in a few segments of your post and it's likely
others may not understand some of it either.

---

### Post by jdc.84 on 2008-12-09
Ah right thanks a lot. 
I removed Wine from Terminal with the command you gave me, however i just thought i'd see if it had deleted the Wine directory my "home" folder on the HDD... the ".wine" folder is still there will all its contents.

Should i delete this folder before i reinstall?
Or will the re-installation see the folder and accept it?

---

### Post by hikaricore on 2008-12-09
It will accept it, but if you've already messed something up in that folder you may still have problems after reinstallation.
I personally never remove my WINE folder nor do I usually advise others to do so, however if it's not too much trouble you should probably consider it.

You may want to let us know what it is you installed after installing WINE so anyone who reads it might have a better idea of your troubles. :)

---

### Post by jdc.84 on 2008-12-09
Reety then,

I completely deleted the .wine folder in the home directory.

Installed wine once again.

Still wine is not visible anywhere in the apps menu.

The program i am trying get running is AutoCAD 2000, i found from another user a page to help: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=102&iTestingId=26162](http://appdb.winehq.org/objectManager.php?sClass=version&iId=102&iTestingId=26162)

However after this fresh installation of wine, right clicking on the setup.exe file on the AutoCAD CD doesn't offer a run in wine. Furthermore when i click find other programs Wine isn't there.

Any ideas?? (It's now half one and i've had enough for this eve)

---

### Post by jdc.84 on 2008-12-09
Sorry take that last bit back, i can load the setup file in wine.

Its still not in the apps menu though.


Anyway thanks for the help

---

### Post by albinootje on 2008-12-09
Which Ubuntu-release are you using ?
And is the Wine-version from packages from ubuntu or from winehq ?
Is your /home mounted with special mount options perhaps ?

---

### Post by jdc.84 on 2008-12-09
Hi, i'm using the latest Ubuntu version.
No i do not think that it has any special mountings. I have absolutely no idea what's going on with it. Quite annoying really because now when ever i want to load the config page for wine i have to go through the terminal... kind of defeats the point of the GUI of Ubuntu.


Anyway, the following instructions to install AutoCAD 2000 using Wine 1.0.1 on Ubuntu 8.10 works:

__________________________________________________________________________
by xaser on Wednesday June 21st 2006, 11:32
HOWTO Install AutoCAD 2000 on LiNUX-Debian-Knoppix5.0.1+Wine0.9

1)Install Wine 0.9
2)Install winetools
3)Use wintools and install a w98 system and all updates possible.
4)Install Acad 2000 (using "open with" option on konkeror over setup.exe, and type wine, in short: open setup.exe with wine)
5)after finnish install copy all the files & libs from the ACAD dir on the acad installer cd to the following wine directories: windows, system32 (was the only way found that always make Acad to found all the libs all the time)
6)copy the fonts from a W98 fonts dir to the wine font dir.
7)Chech that the dir windows on wine install have the msvcrt.dll library present.
8)run by desktop icon created by Acad and Wine.

this was the procedure to got me working acad install, since other install helps was somewhat partial info and well detailed so I was almost mad because had to repeat ful procedure 12 times before got this install sequence working.

If things goes wrong, uninstalls acad2000 by uninstall option of winetools AND then by hand and with konkeror search /.wine dir inside your user dir and then erase the acad200 that was left behind by the uninstall winetools option, and that is inside program files of the wine directory. After a long test, I have it working on and old IBM ThinkPad 600E (pentium II with around 200k memory and IT WORKS VERY Fast and well, in fact the Zooming & Panning feels similar fast than the same machine in the acad2k test install over the W98 installed partition.

Good Luck and patience.
__________________________________________________________________________


If anyone does think of a reason for Wine not being visible i would really like to know. 
Thanks,
John.

---

### Post by jdc.84 on 2008-12-09
Oh and i got Wine from the Add/Remove within the Apps menu in Ubuntu.

---

