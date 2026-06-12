---
title: "Help downloading WoW Wine keeps denying it"
date: 2010-11-30
forum: Wine
---

### Post by SilentMidnitez on 2010-11-30
Sooo I'm a fairly new ubuntu/linux user. I downloaded and installed wine. Next I went to start downloading the client for windows. It let me download the downloader but it refused to let me use it. "The file '/home/family/Downloads/WoW-4.0.0-WOW-enUS-Installer (1).exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.." Help??

---

### Post by apostra on 2010-11-30
Hey mate,

right click-> properties-> permissions-> tick "Allow executing file as program"

that would be all

have fun

---

### Post by SilentMidnitez on 2010-12-02
Thanks pal but now I downloaded WoW on the Vista side of my partition, now i need to figure out how to pull the files over my partition, I once discovered how to do it, but i cannot remember.

---

### Post by northd_tech on 2010-12-04
> **SilentMidnitez said:**
> Thanks pal but now I downloaded WoW on the Vista side of my partition, now i need to figure out how to pull the files over my partition, I once discovered how to do it, but i cannot remember.
Have you tried the "NTFS Configuration Tool" under the System menu?  It should usually tell you something about "new partitions found" when the Vista partition is mounted and you can then change your preferred options (or else cancel out of that "new partitions" window to get to the Configuration Tool window). 

Depending upon if you have external drives, you might want to "Enable write support for external device" and/or "Enable write support for internal device."

You will probably want to click "Advanced Configuration" then if you tick those partition(s) as writable, they should automatically be mounted the next time you restart Ubuntu (even if they are external drives- they just need to be powered up and have a USB cable connected).  I've got 4 external partitions and 1 internal Vi$ta partition set up this way and they work perfectly (in fact I often need to use Linux to "fix" files that Vi$ta won't let me work with or delete).  The hard disk partitions act just like really-big USB thumb drives this way, and you can cut/copy/paste using Ubuntu to move/copy/delete files.

Edit:  Of course, you can **REALLY SCREW UP VISTA from Linux** if you aren't **absolutely sure** of what files you are messing with- so go well-warned on that part.

---

### Post by apostra on 2010-12-04
Hey mate,

you can use a usb stick, or external HDD to do the transfer as well.

I did this once. Remember to delete the WTF folder before launch it and make it executable and run on wine from right click properties and run it with opengl as well.

Have fun

---

### Post by cwwilson721 on 2010-12-04
A *MUCH* easier way is to :
[LIST]
[*]Open the folder where you want to install WoW (usually /home/<USER>/.wine/drive_c/Program Files/World of Warcraft)
[*]Open the folder on the Windows drive where WoW is installed (Easiest is Places > <WINDOWS DRIVE>)
[*]In the Windows/WoW folder, click Edit > Select All, and drag the files to the opened WoW/Linux folder
[*]Create a Launcher for the WoW Lancher.exe. Right click the Desktop, 'Create Launcher'. and use the following command in the 'command' box:```
env WINEPREFIX="/home/<USER>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```Replace the icon with one of your own choosing.
[/LIST]Note: all '<CAPS>' is to be replaced by your own names,etc.

That ought to get you going. I'd personally delete the config.wtf file in the 'new' wine/WoW install to be sure of no conflicts. It will recreate itself the first time you run WoW.

Good luck.

---

