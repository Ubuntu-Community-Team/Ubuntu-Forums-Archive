---
title: "Wine won't install anything anymore"
date: 2010-06-20
forum: Wine
---

### Post by ewientje on 2010-06-20
Hi I have Wine, PlayonLinux installed, but now Wine won;t install any program any more.
The games and programs I have working are StarWars Jedi Knight, StarTrek Elite Force, terragen, Uru Live, Adobe Digital Editions, Microsoft reader, and MMB.

I would like to install artrage-studio, but I click on a exe file, first it said that I didn't have permission, now it just hangs, and does nothing.

I have Ubuntu 10

---

### Post by ronnielsen1 on 2010-06-20
I might get bashed here but that's been my experience with playon linux. I prefer to stay with wine and check winehq for the application in question. PlayOnLinux and wine don't play well with each other IMHO

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18783](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18783)

---

### Post by ronnielsen1 on 2010-06-20
> wine is a excellent system!wasn't bad mouthing wine, was talking about PlayOnLinux

In my opinion, I would uninstall PlayOnLinux, see if wine works (if not, reinstall) and then install artrage-studio as described in [http://appdb.winehq.org/objectManage...sion&iId=18783]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18783")

> Needs 'gdiplus'. The demo version also needs 'corefonts'.   Almost everything works, minor visual issues. 
**What does not**

 Installer :      
  workaround is to run the installer, copy the extracted msi  from drive_c/users/USERNAME/Application Data/Ambient Design/ArtRage  Studio Pro/install/ and run it with 'msiexec /i'.    Auto updater :      
  very minor issue, the updated installer is available for manual  download. 
**What was not tested**
Photoshop Filters 

**Additional Comments**

Tool settings, layers and all other floating transparent windows have a black border around them.

If the cursor is sluggish, set "HKEY_CURRENT_USER > Software > Wine > X11_Driver > ClientSideWithRender" to "N", in regedit. (thx meho_r)



---

### Post by ewientje on 2010-06-20
Ok, thank you, I'll give it a try.

I unistalled playonlinux, now startrek won;t start anymore either.
I will uninstall wine, and reinstall wine now.

---

### Post by jchase45 on 2010-06-20
The version of wine with play on linux is 1.14, so it's old and out of date , uninstall them both , follow these directions here 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

that will give you the latest wine (1.2 rc) on your Ubuntu software center.

---

### Post by ewientje on 2010-06-22
I did that, now several programs which used to work have stopped working.

edited, well I have gotten several programs working again, I can install programs from Cdrom or Iso, but not an exe which sits on the harddrive.

---

### Post by ronnielsen1 on 2010-06-23
> but not an exe which sits on the harddrive

Right click > Properties > Mark file as executable

> I prefer to stay with wine and check winehq for the application in   question. 	
Me too

---

### Post by ewientje on 2010-06-23
I already marked artrage as an executable.
But I'll check winehq, thanks everyone.

---

