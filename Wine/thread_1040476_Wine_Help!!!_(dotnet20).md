---
title: "Wine Help!!! (dotnet20)"
date: 2009-01-15
forum: Wine
---

### Post by RikerE on 2009-01-15
Well, i've changed, altered, searched and meddled the past day or two working at this and have gotten ABSOlUTELY NOWHERE, so hopefully someone on here can help.

To start, i have Ubuntu 8.04 so far, im sticking to LTS for now...

I found a tutorial about how to install Microsoft Office 2007, i have had several errors occur:

1. Can not install dotnet20 , that i think is the biggest problem...

2. Installer USED to run half-way then crash saying "can not find onenote" and to browse to it, i did so and it didn't except that...

3. Now the installer just crashes at the half-way point...

Any help would be nice, i've done everything from using a few dll's from a VISTA pc i own to changing settings around....

---

### Post by 655 on 2009-01-15
Read this entry on the Wine appDB for general installation help, and the subsequent entries for Office suite apps: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

Read this thread: [http://www.winehq.org/pipermail/wine-users/2006-September/023488.html](http://www.winehq.org/pipermail/wine-users/2006-September/023488.html)

This thread suggests that using winetricks will install dotnet 2.0 correctly: [http://forum.winehq.org/viewtopic.php?t=3254&sid=5de83626718b649a6ba1fac95cb0fbc1](http://forum.winehq.org/viewtopic.php?t=3254&sid=5de83626718b649a6ba1fac95cb0fbc1)

Try going back to that step and getting dotnet working, then see what else happens.  I don't use either of the programs in question, so this is just hearsay from what I googled up.  The two problems may be unrelated.  In any case, do use the winehq site because many problems are documented.

---

### Post by RikerE on 2009-01-17
Im still getting nowhere with MS-Office...

If i were to run the installer on a win. pc and move the files onto my Ubuntu Pc would it work? Or does it conceal some counter-measure in the win. Reg? 

(i found out about them trying to put Photoshop on my flash-drive:P)

---

### Post by 655 on 2009-01-17
What version of Wine are you running? Do this to check:
 
```
wine --version
```If you are using the latest dev build, it is 1.1.13, and it will install without any hacks or tricks, according to the WineHQ AppDB entry I referred you to earlier.  If you are using an earlier version of Wine (the latest stable version is 1.0), do the following, reposted from the AppDB entry ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992):]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992%29:")

> [SIZE=1]In current (1.1.3 or newer) Wine, simply install as you would in Windows: insert the cd, and run setup.exe. **No overrides are needed to install in Wine 1.1.3 or later. **
[/SIZE]     
   [SIZE=1]If using a version of Wine older than 1.1.3, these howtos may be helpful:[/SIZE]
   
[LIST]
[*][SIZE=1]Quick Tweaks: [Install MS Office 2007 in Linux]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/#more-5") (Danger! Don't download DLLs from random sites on the internet, as this recipe advises! See [the Wine FAQ]("http://wiki.winehq.org/FAQ#head-bb6a7a98ea5016383c4f81717063463e5217c3bf").) [/SIZE]
[*][SIZE=1]Wine Review: [Office 2007 on Linux with Wine install guide]("http://wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html") (This one is safer; it only has you download .dlls from Microsoft.com and Codeweavers.com.)[/SIZE]
[/LIST]
Those how-tos are clickable links btw.  Note that, once installed, you are going to have to do special things to run it.  See the AppDB entry above.

Alternatively, try VMWare ([http://www.vmware.com/](http://www.vmware.com/)) if you don't like that degree of configuration.

---

### Post by RikerE on 2009-01-20
Sorry for taking long to get back on here, im still not getting anywhere,

according to that command i have wine

wine-1.1.12

Synaptics Package Manager says this is the latest, i even ran the updater and it said the same...

I found on one site that some had patches to run via "/adminfile patch.msp"

I tried that, and it appeared to work, but could not locate "excel.en-us" which is on the disk......

Though all my other stuff runs fine, even Game-maker, a program which has a long history of INCOMPATABILITY...

---

