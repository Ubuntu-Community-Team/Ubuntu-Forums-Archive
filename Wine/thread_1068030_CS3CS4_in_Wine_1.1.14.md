---
title: "CS3/CS4 in Wine 1.1.14?"
date: 2009-02-12
forum: Wine
---

### Post by MasterNetra on 2009-02-12
Anyone know if Adobe Flash Pro/Master CS3 and/or Adobe Flash Pro/Master CS4 installs in Wine 1.1.14? I know it didn't in the prior versions. Also anyone know if it works any better in 1.1.14? (And yes i did check the App Databaase, CS3 hasn't been updated sense 1.1.4 for flash pro)

---

### Post by donkyhotay on 2009-02-12
> **MasterNetra said:**
> Anyone know if Adobe Flash Pro/Master CS3 and/or Adobe Flash Pro/Master CS4 installs in Wine 1.1.14? I know it didn't in the prior versions. Also anyone know if it works any better in 1.1.14? (And yes i did check the App Databaase, CS3 hasn't been updated sense 1.1.4 for flash pro)

If you want to know if it will install or not you should check out this:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8646](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8646)
This is an appdb entry specific for the cs3/4 installer. As a maintainer I've been able to install every cs4 program except for acrobat (which just fails to install) and illustrator (which crashes wine during install). Now if you want to know if it will work correctly after installation, well that is a completely different issue.

---

### Post by donkyhotay on 2009-02-12
Out of curiousity I downloaded the trial and tried running it. It installed perfectly but crashed when I tried launching the program. Admittedly this was on a VM I use for testing which only has 1gb of RAM which is the minimum requirements on a normal windows box. If you want more information you'll either need to wait for someone else to post or try downloading and installing the trial yourself.

---

### Post by MasterNetra on 2009-02-15
I tried to install CS3 i got that gecko thing installed correctly as well as msxml6 and ie6... (installing the msxml6 in turn got ie6, a twofur :p) only the autorun loader runs. AFter clicking on install within the autoloader window it simply closes out or crashes i guess you could say. Going straight to setup on the cd results in the same thing it seems... Of course at the same time I'm using a backup image that i have stored (i accidentally stepped on my original >.<) and i know the backup is good because when i was using windows i downloaded it from where i store my backups online and i was able to mount it and install it within windows. (Apparently not much luck in Ubuntu atm).

---

### Post by alex.rayu on 2009-02-16
Very strange. I also fail to install CS3, but mostly because if crashes the installer when installing the shared components.

There is 1.1.15 available now - has a number of fixes pertaining to our issues. I don't think that fixes my intel graphics card problem though.

---

### Post by MasterNetra on 2009-02-16
> **alex.rayu said:**
> Very strange. I also fail to install CS3, but mostly because if crashes the installer when installing the shared components.

There is 1.1.15 available now - has a number of fixes pertaining to our issues. I don't think that fixes my intel graphics card problem though.

Yea I'm waiting for 1.1.15 to become available in repo :/

---

### Post by alex.rayu on 2009-02-17
I have cloned GIT repository and compiled the latest Wine from GIT. I will be doing that daily.

The improvements are obvious, but I am saddened to say that the intel GMA integration with Wine has not been fixed. 

wine: Call from 0x7edfe8b0 to unimplemented function gdiplus.dll.GdipMeasureDriverString, aborting

Thus, I ahev not been able to test the CS4 =)

---

### Post by donkyhotay on 2009-02-17
> **alex.rayu said:**
> wine: Call from 0x7edfe8b0 to unimplemented function gdiplus.dll.GdipMeasureDriverString, aborting

Have you tried installing gdiplus with winetricks?

---

### Post by alex.rayu on 2009-02-17
Yes, numerous times from as early as 1.1.11

When I use winetricks gdiplus, it crashes even faster, on memory read error. I submitted both variants of error log to wine bugzilla.

---

### Post by MasterNetra on 2009-02-17
Well I'm not too worried about CS4, but i would hope to get CS3 installed...Curious does CS3 need a encryption emulator like daemon tools to properly load the CD because with windows i used Daemon tools to mount my backup CD image to install it. I just now realized that possibility >.< And if so any mounting programs for Ubuntu you recommend to handle it?

---

### Post by alex.rayu on 2009-02-17
There is GMount-iso for Gnome to mount images.

---

### Post by donkyhotay on 2009-02-17
The adobe installer doesn't actually need the disc during installation. It's possible to copy all files from the disc(s) onto the hard drive and run setup directly from there. This of course is assuming you actually have the physical discs.

---

### Post by MasterNetra on 2009-02-18
> **donkyhotay said:**
> The adobe installer doesn't actually need the disc during installation. It's possible to copy all files from the disc(s) onto the hard drive and run setup directly from there. This of course is assuming you actually have the physical discs.

I did mention in post 4 that i was using a backup **image**. I'm just trying to figure out why CS3 won't install even after getting IE6 and using winetricks to get something else installed (i forget what atm). Everytime I get to setup the installer crashes. Autorun brings up the popup to install it though.

---

### Post by alex.rayu on 2009-02-18
Stardate 18022009. CS3 does not install - regardless of CD image or not. I have read in the forums, that thing also sometimes happens on Mac and Windows. That never happened to me with CS3 under Windows. I was not able to identify the problem. Starfleet admiral Picard advised to abandon efforts on that one and concentrate on CS4.

---

### Post by donkyhotay on 2009-02-19
I would recommend not using an image but extracting all the files in the image onto the desktop and running directly. Also run the setup program not the autorun launcher. That was the point I was trying to make. I disagree with alex.rayu on cs3 being impossible to install. I've found he cs3 installer actually works better then the cs4 variant. However I do agree you should probably focus on cs4 because the amount of effort is going to be pretty much the same and you might as well aim for compatibility with windows/osX users.

---

### Post by MasterNetra on 2009-02-20
Trying to install it after extract still failed.. And i had tried setup itself when it was in image. (And yes I tried it while it was extracted)

---

