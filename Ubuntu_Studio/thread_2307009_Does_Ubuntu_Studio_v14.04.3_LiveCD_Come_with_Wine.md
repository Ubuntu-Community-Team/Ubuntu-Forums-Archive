---
title: "Does Ubuntu Studio v14.04.3 LiveCD Come with Wine?"
date: 2015-12-21
forum: Ubuntu Studio
---

### Post by yoshii on 2015-12-21
EDIT:  Solved--Wine isn't installed but see the post further down on how to do an offline install of Wine from within an existing online installation.  

Does the Ubuntu Studio v14.04.3 LiveCD come with Wine?  
I am wondering because I will be moving soon and won't have internet access anymore and I am also getting a new computer that I will be putting Ubuntu Studio onto.  
Also, is there a list somewhere of all the software on Ubuntu Studio's ISO so I know what I'm getting?

---

### Post by Bucky Ball on 2015-12-21
Research [here]("https://wiki.ubuntu.com/UbuntuStudio/PackageList") and [here]("https://wiki.ubuntu.com/UbuntuStudio/PackageList") and [this search]("http://ubuntustudio.org/?s=wine") might tell you something. I very much doubt it.

Also, please see second link in my signature. You'll probably get questions like this answered sooner. :)

---

### Post by yoshii on 2015-12-22
Those resources were old and out of date but [http://winehq.com](http://winehq.com) explained how to do an offline install from within an existing Ubuntu install, so I got the Wine .deb archives.  
Essentially, what you do is clear the apt cache using "sudo apt-get clean" and then immediately redownload wine and copy the .deb's out of /var/cache/apt/ onto a removeable flash drive.  

It's a little bit tricky because to install wine, it removed my old wine, so I had to make sure I wasn't messing anything up.  And the new wine (v1.8) installs into a different location than before and removes the menu listing for wine config (winecfg).  As it turns out, the new location of wine is /opt/wine-devel/ so I found winecfg inside the /bin folder in there.   Luckily, everything runs as normal so you don't have to remap your .desktop launchers or anything.

---

